---
title: "Asterisk on 9.10 and Script assistance"
date: 2009-12-23
forum: General Help
---

### Post by sr_guy on 2009-12-23
There is a known timing issue with zaptel and Ubuntu versions 9.04 through the latest versions. Unfortunantly, the bug is not being fixed in the distros themselves nor synaptic updates. The biggest issue with the timing issue is inability to play SIT tones so to use the built in call blocking function in FreePBX.

see: [http://ubuntuforums.org/showthread.php?t=1144894](http://ubuntuforums.org/showthread.php?t=1144894)


I modified a script to install asterisk, components, and freepbx with a section to install the zaptel patch to correct the timing issue, but it still has not corrected the issue. Can any kind soul that has asterisk/freepbx on 9.04 or newer, and has some script knowledge take a look and see if I am missing something in the below script? The section that contains the zaptel patch is listed under "#install zaptel" section.

```

#!/bin/bash
#
# This script to install the Dahdi drivers, Asterisk and FreePBX
# on a new install of ubuntu 9.04 (Jaunty Jackalope).
#
# Must be run with superuser privileges.
#
# Includes known required fixes and patches from the 9.04 install.
# There is no error checking here, but it is known to work on a base
# install as of 18 Ago 09, with Ubuntu 9.04 and downloaded versions of:
# asterisk-1.6.0.13 (or other 1.6 current)
# asterisk-addons-1.6.0.3 (or other 1.6 current)
# freepbx-2.5.1
# libpri-1.4.10.1
# dahdi-linux-2.2.0.2 (or current)
# dahdi-tools-2.2.0 (or current)
#
# script version version 1.2 released at 18 Ago 09
# Comments and suggestions very welcome.
#
# Updates, and tips can be found at:
# http://wiki.ubuntu.com/AsteriskOnUbuntu/
#
# Good Luck!
#
# Asterisk On Ubuntu Team
# Peter N. Steinmetz (ndoc2@steinmetz.org)
# Duda Nogueira (dudanogueira@ubuntu.com)
#
# Changelog:
# 1.2 - Added mpg123 and php5-curl as dependency
# Added link to fix music on hold (moh)
# Replaced zaptel by dahdi
# 1.1 - First release


# definitions of items to possibly change
export *****=******
export FREEPBX_VERSION=2.5.1
export ceaf877t=ceaf877t
export IP_ADDRESS=192.168.1.7

# ensure package directory up to date and system upgraded
apt-get -y update
apt-get -y upgrade

# retrieve utilities and set debconf to noninteractive front-end
apt-get -y install debconf-utils
debconf-set-selections <<CONF_EOF
debconf debconf/frontend select noninteractive
CONF_EOF

debconf-set-selections <<CONF_EOF
debconf debconf/frontend select Dialog
CONF_EOF

# install packages needed beyond base install with openssh server
apt-get -y install linux-headers-`uname -r` --force-yes
apt-get -y install make bison flex g++ gcc apache2 php5 php5-curl
apt-get -y install php5-cli php5-mysql php-pear php-db php5-gd curl
apt-get -y install sox libncurses5-dev libssl-dev libmysqlclient15-dev
apt-get -y install mpg123
#clear

# place source packages in standard place
cd /usr/src

# download, make, install, and configure dahdi drivers
wget http://downloads.digium.com/pub/telephony/dahdi-linux/dahdi-linux-current.tar.gz
tar -xvzf dahdi-linux-current.tar.gz
cd dahdi-linux*
make clean
make
make install
cd ..
#clear

# download, make, install, and configure dahdi tools
wget http://downloads.digium.com/pub/telephony/dahdi-tools/dahdi-tools-current.tar.gz
tar -xvzf dahdi-tools-current.tar.gz
cd dahdi-tools*
make clean
./configure
#make menuselect
make
make install
make config
cd ..
#clear

# download, make and install libpri
wget http://downloads.digium.com/pub/libpri/libpri-1.4-current.tar.gz
tar xfz libpri-1.4-current.tar.gz
cd `find . -name "libpri-1.4.*" -print`
#./configure
make install
cd ..
#clear

# download, make and install asterisk and configuration files
wget http://downloads.digium.com/pub/asterisk/asterisk-1.6.0-current.tar.gz
tar xfz asterisk-1.6.0-current.tar.gz
cd `find . -name "asterisk-1.6.0.*" -print`
./configure
make install
make samples
cd ..
#clear

#install zaptel
cd /usr/src
wget http://downloads.asterisk.org/pub/telephony/zaptel/zaptel-1.4.12.1.tar.gz
tar xzf zaptel-1.4.12.1.tar.gz
cp /usr/src/patch.diff /usr/src/zaptel-1.4.12.1/kernel
cd /usr/src/zaptel-1.4.12.1/kernel
patch < patch.diff
cd /usr/src/zaptel-1.4.12.1
./configure
make clean
make
make install
make samples
cd ..
#clear

# download, make and install asterisk-addons
wget http://downloads.digium.com/pub/asterisk/asterisk-addons-1.6.0-current.tar.gz
tar xfz asterisk-addons-1.6.0-current.tar.gz
cd `find . -name "asterisk-addons-1.6*" -print`
./configure
make install
cd ..
#clear

# download and install extra asterisk sounds
mkdir asterisk-sounds
cd asterisk-sounds
wget http://downloads.digium.com/pub/telephony/sounds/asterisk-extra-sounds-en-gsm-current.tar.gz
tar -zxf asterisk-extra-sounds-en-gsm-current.tar.gz
cp -rf * /var/lib/asterisk/sounds
cd ..
#clear

# create asterisk user and group, adding to www-data group for apache server
adduser asterisk --disabled-password --gecos "asterisk PBX"
adduser www-data asterisk

# fix up apache configuration to run as asterisk user
cp /etc/apache2/apache2.conf /etc/apache2/apache2.conf-orig
sed -i "s/\(^User *\)\(.*\)/\1asterisk/" /etc/apache2/apache2.conf
sed -i "s/\(^Group *\)\(.*\)/\1asterisk/" /etc/apache2/apache2.conf

# patch safe_asterisk script to use bash
sed -i "s|#!/bin/sh|#!/bin/bash|" /usr/sbin/safe_asterisk

# add asterisk startup item
cat > /etc/init.d/asterisk <<-END_STARTUP
#!/bin/bash
set -e
set -a
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DESC="Asterisk"
NAME=amportal
DAEMON=/usr/sbin/\$NAME

test -x \$DAEMON || exit 0

d_start() {
amportal start
}

d_stop() {
amportal stop
}

d_reload() {
amportal restart
}

case "\$1" in

start)
echo -n "Starting \$DESC: \$NAME"
d_start
echo "."
;;

stop)
echo -n "Stopping \$DESC: \$NAME"
d_stop
echo "."
;;

restart|force-reload)
echo -n "Restarting \$DESC: \$NAME"
d_stop
sleep 10
d_start
echo "."
;;

*)

echo "Usage: \$SCRIPTNAME {start|stop|restart|force-reload}" >&2
exit 3
;;

esac

exit 0
END_STARTUP

chmod 755 /etc/init.d/asterisk
update-rc.d asterisk defaults 90 10

# download and unpack freepbx
wget http://mirror.freepbx.org/freepbx-2.5.1.tar.gz
tar -xzf freepbx-2.5.1.tar.gz


# configure freepbx
cd freepbx*

# setup databases for freepbx use
mysqladmin -u root -p${****} create asterisk
mysqladmin -u root -p${****} create asteriskcdrdb
mysql -u root -p${****} asterisk < SQL/newinstall.sql
mysql -u root -p${****} asteriskcdrdb < SQL/cdr_mysql_table.sql
mysql -u root -p${****} <<-END_PRIVS
GRANT ALL PRIVILEGES ON asterisk.* TO asteriskuser@localhost IDENTIFIED BY "${ceaf877t}";
GRANT ALL PRIVILEGES ON asteriskcdrdb.* TO asteriskuser@localhost IDENTIFIED BY "${ceaf877t}";
flush privileges;
END_PRIVS

# reconfigure php for freepbx
cp /etc/php5/apache2/php.ini /etc/php5/apache2/php.ini-orig
sed -i "s/\(upload_max_filesize *= *\)\(.*\)/\120M/" /etc/php5/apache2/php.ini
sed -i "s/\(memory_limit *= *\)\(.*\)/\1100M/" /etc/php5/apache2/php.ini
sed -i "s/\(magic_quotes_gpc *= *\)\(.*\)/\1Off/" /etc/php5/apache2/php.ini

# fix up directory use and permissions for asterisk
mkdir /var/run/asterisk
chown asterisk:asterisk /var/run/asterisk
chown asterisk:asterisk -R /etc/asterisk
chown asterisk:asterisk -R /var/lib/asterisk
# chmod a+x /var/lib/asterisk/bin/*
chown asterisk:asterisk -R /var/log/asterisk
chown asterisk:asterisk -R /var/spool/asterisk
chown asterisk:asterisk -R /var/www
sed -i "s/\[directories\](!) .*/[directories]/" /etc/asterisk/asterisk.conf
sed -i "s|astrundir *=> */var/run|astrundir => /var/run/asterisk|" /etc/asterisk/asterisk.conf

# start asterisk
./start_asterisk start

# configure amportal
cp amportal.conf /etc/amportal.conf
sed -i "s/# \(AMPDBUSER=asteriskuser\) */\1/" /etc/amportal.conf
sed -i "s/# \(AMPDBPASS=\).*/\1${ceaf877t}/" /etc/amportal.conf
sed -i "s|\(AMPWEBROOT=\)/var/www/html|\1/var/www|" /etc/amportal.conf
sed -i "s|\(FOPWEBROOT=\)/var/www/html/panel|\1/var/www/panel|" /etc/amportal.conf
sed -i "/#AMPWEBADDRESS=192.168.1.101/d" /etc/amportal.conf
sed -i "s/AMPWEBADDRESS=/AMPWEBADDRESS=${IP_ADDRESS}/" /etc/amportal.conf
#clear

# install amp
./install_amp

# start apache web server
/etc/init.d/apache2 restart

# load up dahdi drivers
/etc/init.d/dahdi start

# freepbx/asterisk points to other direction
# when searching for music on hold, let's fix it!
ln -s /var/lib/asterisk/moh /var/lib/asterisk/mohmp3

# start amportal
amportal start

clear
# voila!
echo "#####################################################"
echo " "
echo " Now, point your browser to:"
echo " `${IP_ADDRESS}`/admin"
echo " Also, check: http://wiki.ubuntu.com/AsteriskOnUbuntu"
echo " to learn how to fine tune you PBX!"
echo " "
echo "bye! Ubuntu Asterisk Team!"


```

---

### Post by manickaselvam on 2010-02-02
Hi... Did your problem solved...? If so you please help me... I'm trying to install zaptel in my ubuntu9.10...!!!

Manick

---

### Post by sr_guy on 2010-02-02
I ended up doing this to solve it:

```

cd /usr/src

svn co http://svn.digium.com/svn/asterisk/branches/1.6.1/ asterisk
svn co http://svn.digium.com/svn/asterisk-addons/branches/1.6.1/ asterisk-addons

----------------------------

cd asterisk
./configure
nano -w Makefile
(change all instances of "ASTVARRUNDIR=<something>" to "ASTVARRUNDIR=/var/run/asterisk". If you know a better way, please point it out)
make
sudo make install

cd asterisk-*
make
make install

-------------------------------

#Asterisk 1.6 config
nano -w /etc/asterisk/sip_general_custom.conf
session-timers=refuse

reboot

#Setup Ports
sudo nano -w /etc/asterisk/rtp.conf

rtpstart=10000
rtpend=10100

---------------------------------

sudo nano -w /etc/init.d/asterisk

Copy the init file from here, save. 

http://www.joeterranova.net/wiki/index.php?title=Asterisk-init


sudo chmod +x /etc/init.d/asterisk
sudo chown -R asterisk:asterisk /var/spool/asterisk/ /var/log/asterisk/
sudo update-rc.d asterisk defaults
sudo /etc/init.d/asterisk start

-----------------------

#Mysql Permissions
mysqladmin -uroot -p create asterisk create asteriskcdrdb
echo "GRANT ALL PRIVILEGES ON asterisk.* TO asterisk@localhost IDENTIFIED BY '<asteriskpassword>';" | mysql -u root -p
echo "GRANT ALL PRIVILEGES ON asteriskcdrdb.* TO asterisk@localhost IDENTIFIED BY '<asteriskpassword>';" | mysql -u root -p
Configure Asterisk Files:
sudo nano -w /etc/apache2/apache2.conf
User asterisk
Group asterisk
sudo nano -w /etc/asterisk/asterisk.conf
astrundir => /var/run/asterisk
sudo nano -w /etc/php5/apache2/php.ini
sudo nano -w /etc/php5/cli/php.ini
post_max_size = 20M
upload_max_filesize = 20M
magic_quotes_gpc = Off
memory_limit = 100M

sudo /etc/init.d/apache2 restart

--------------------------


# Get DAHDI Tools / Complete

cd /usr/src
svn co http://svn.digium.com/svn/dahdi/linux-complete/trunk/ linux-complete

cd linux-complete/linux

make
make install

cd linux-complete/tools
./configure
make
make install

```

In particular installing dahdi and dahdi tools.

---

