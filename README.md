# mymcda-c

# Como instalar o Laravel do Zero
Para que se consiga instalar o Laravel do Zero, deve-se seguir os seguintes procedimentos:
1) https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-22-04
2) https://www.digitalocean.com/community/tutorials/how-to-install-linux-nginx-mysql-php-lemp-stack-on-ubuntu-22-04
3) https://www.digitalocean.com/community/tutorials/how-to-install-and-use-composer-on-ubuntu-22-04
4) https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-laravel-with-nginx-on-ubuntu-22-04

# Configuração básica do servidor para rodar o MyMCDA-C
## 1. Configuração inicial do servidor Ubuntu 22.04
### 1.1 Conectar com servidor como superusuário _root_
```Linux
$ ssh root@your-server-ip
```
Obs.: Não se esqueça de substituir o ***_your-server-ip_*** pelo ip do seu servidor.

### 1.2 Criando um novo usuário
O superusuário tem amplos poderes dentro do servidor Linux. Assim, é importante que não se deixe sua senha exposta ou que você tenha um usuário de backup para resolver algum problema que possa se ter no futuro.

```
# adduser new-user
```
Obs.: Substituir o new-user pelo nome do novo usuário.

### 1.3 Atribuindo privilégios administrativos
O comando abaixo deve ser realizado como superusuário ***root*** para atribuir os privilégios administrativos ao usuário recém criado.

```
# usermod -aG sudo new-user
```

## 2. Instalando Nginx, MySQL, PHP e Laravel
Antes de fazer a instalação do NGinx, MySQL e PHP, vamos atualizar o sistema operacional.

```
$ sudo apt-get upgrade
$ sudo apt-get update
```

### 2.1 Instalando o Nginx
Com o sistema atualizado, vamos instalar o Nginx

```
$ sudo apt-get install nginx
```

Para testar a instalação do nginx, vamos descobrir o ip da máquina. Para isso, vou pode usar qualquer um dos dois comandos abaixo:

```
$ ip addr show
$ hostname -i
```

Para testar a instalação do nginx, abra o navegador e acesse o site:

```
http://seu-ip
```
Obs.: Troque o ***seu-ip*** pelo ip da sua máquina

### 2.2 Instalando o MySQL
A instalação do MySQL exige algumas configurações importante. Preste a atenção nos comandos para não ter erro.
Comece fazendo a instação com o seguinte comando:

```
$ sudo apt install mysql-server
```

Antes de fazer a configuração do mysql_secure_installation, executar os comandos abaixo:
```
$ sudo mysql
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'insert_password';
exit;
```

## 3. Configurações iniciais Laravel
