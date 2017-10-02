# apache-extauth-modulekit
Script for using Apache External auth with modulekit-auth

The `check_user` script will read username and password from stin and exit with
an exit code of '0' when the user authenticated successfully.

# Installation
```sh
sudo apt-get install libapache2-mod-authnz-external php-cli
sudo a2enmod authnz_external
git clone https://github.com/plepe/apache-extauth-modulekit.git
cd apache-extauth-modulekit
git submodule init
git submodule update
cp conf.php-dist conf.php
nano conf.php # adapt to your needs
```

# Apache Configuration
```apache
<Directory /var/www/securearea>
AuthType Basic
AuthName "Restricted"
AuthBasicProvider external
AuthExternal special-auth
require valid-user
</Directory>

AddExternalAuth special-auth /path/to/apache-extauth-modulekit/check_user
SetExternalAuthMethod special-auth pipe
```
