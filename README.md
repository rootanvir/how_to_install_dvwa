# How to install dvwa in kali 

## 1.go to /var/www/html
```bash
cd /var/www/html
```
### 2.download dvwa
```bash
sudo git clone https://github.com/digininja/DVWA.git
```
## 3.give permission

```bash
sudo chmod -R 777 DVWA
```
## 4.goto dvwa
```bash
cd DVWA
```
## 5.Copy because we will keep an copy
```bash
cp config.inc.php.dist config.inc.php
```
## 6.open ```config.inc.php``` with mousepad
- ```bash
   sudo mousepad config.inc.php
  ```
- change the user and password
  ```
    $_DVWA[ 'db_user' ]     =   getenv  ('DB_USER') ?: 'admin';
    $_DVWA[ 'db_password' ] =   getenv  ('DB_PASSWORD') ?:   'password';
  ```

## 7.start mtsql and apache2
```bash
sudo service apache2 start
sudo service mysql start 
```
## 8.go to superuser
```bash
sudo su
```

## 9.go to mysql
```bash
mysql -u root -p
```
- press enter
  

  - create database 
- ``` bash
  create database dvwa;
  ```
  - create user
- ``` bash
  create user 'admin'@'127.0.0.1' identified by 'password';
  ```
  - grant all permission to the user
- ``` bash
  grant all privileges on dvwa.* to 'admin'@'127.0.0.1';
  ```
- exit from the mysql
- ``` bash
  exit
  ```

## 10.go to latest version of php directory (min 8.4) 
- ```bash
    cd 8.4
  ```
- ```bash
    cd apache2
  ```
  - open php.ini with your favcourite text editor and On those
- ```bash
    allow_url_fopen = On
    allow_url_include = On
  ```
### 11.restart mysql and apache2 service

```bash
sudo service mysql restart
sudo service apache2 restart
```
## 12.open browser and type ```localhost/DVWA``` or click below
- [localhost/DVWA](http://localhost/DVWA)

### 13. use credential
```c++
Username=admin
Password=password
```
- ##  after login
- goto ```Setup/Reset DB```
- click ```create / Reset Database```
---
## start those service everytime you use them
```bash
sudo service apache2 start
sudo service mysql start 
```