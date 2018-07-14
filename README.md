# WordPress-on-Ubuntu-14.04
sudo apt-get update
sudo apt-get install mysql-server
sudo mysql_secure_installation
sudo mysql_install_db
mysql -u root -p
CREATE DATABASE wordpress;
CREATE USER wordpressuser@localhost IDENTIFIED BY 'PASSWORD_FOR_DATABASE';
GRANT ALL PRIVILEGES ON wordpress.* TO wordpressuser@localhost;
FLUSH PRIVILEGES;
exit
wget http://wordpress.org/latest.tar.gz
apt-get install curl
tar xzvf latest.tar.gz
sudo apt-get update
sudo apt-get install php5-gd libssh2-php
cd ~/wordpress
cp wp-config-sample.php wp-config.php
curl -s https://api.wordpress.org/secret-key/1.1/salt/
*COPY ALL SECURE KEYS*
nano wp-config.php
*PASTE SECURE KEYS*
*CHANGE DB_NAME TO "wordpress"*
*CHANGE DB_USER TO "wordpressuser"*
*CHANGE DB_PASSWORD TO "PASSWORD_FOR_DATABASE"
sudo rsync -avP ~/wordpress/ /var/www/html/
adduser wp
gpasswd -a wp sudo
cd /var/www/html
sudo chown -R wp:www-data *
mkdir /var/www/html/wp-content/uploads
sudo chown -R :www-data /var/www/html/wp-content/uploads
* GO TO http://server_domain_name_or_IP*
