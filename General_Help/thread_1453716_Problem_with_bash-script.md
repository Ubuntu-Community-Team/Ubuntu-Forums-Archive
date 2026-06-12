---
title: "Problem with bash-script"
date: 2010-04-13
forum: General Help
---

### Post by Minky2k on 2010-04-13
Hi! I'm trying to make a automated build-script with bash but i keep getting different errors. Could anyone please tell me what's wrong with this build-script? I'm posing the main build-script and attaching the rest of the scripts in a compressed form.

/Thx

```
#!/bin/bash

gpg --import /home/epm/first_installation/config_chroot_sources_local.gpg
gpg --import /home/epm/first_installation/config_chroot_sources_packages-inl-fr.gpg

echo deb http://www.wzdftpd.net/siem-live lenny main >> /etc/apt/sources.list
echo deb http://packages.inl.fr/debian lenny/ >> /etc/apt/sources.list

apt-get update && echo 'y'

apt-get install ruby ruby-dev gnutls-dev lua50 liblua50-dev libmysqld-dev python-cheetah libpcap-dev libpcre++-dev libpcre++0 liblua5.1-rex-pcre-dev liblua5.1-rex-pcre0 libpcre3 libpcre3-dev cmake make g++ mysql-server

debconf-set-selections /home/epm/first_installation/preseed/prelude

apt-get install libopenscap0 python-prelude libicu42 python-prelude python-preludedb libopenscap0 python flashplugin-nonfree less vim nufw openvas-server openvas-client openvas-plugins-base openvas-plugins-dfsg rng-tools prelude-lml mysql-server dbconfig-common prelude-manager prelude-correlator apache2-mpm-prefork libapache2-mod-python prewikka libxss1 prelude-notify ipython python-openscap libopenscap-perl p0f python-scapy wireshark tshark snort snort-rules-default oinkmaster

#run-parts /usr/share/siem-live/init/
run-parts /home/epm/first_installation/usr/share/siem-live/init

echo Script is DONE!

```

---

### Post by davidpbrown on 2010-04-13
Not an expert but when in doubt I try adding semi-colons to the end of lines;

However, some scripts seem to work fine without, so I've yet to figure out where they are meant to be used.

Certainly with all the logic forks, like if then else, I've got semi-colons on all lines. The simpler scripts are essentially lists of terminal commands, so maybe limit themselves to reading one line. That is, I'm guessing, maybe it's just bash specific instructions that need them.

---

### Post by Minky2k on 2010-04-14
Yeah i've tried that and it still doesn't seem to work. I've done some modifications to the code that should work better...but I still keep getting errors that eludes me, any suggestions? =/

```
#!/bin/bash
gpg --import /home/epm/first_installation/config_chroot_sources_local.gpg
gpg --import /home/epm/first_installation/config_chroot_sources_packages-inl-fr.gpg
#
echo deb http://www.wzdftpd.net/siem-live lenny main >> /etc/apt/sources.list
echo deb http://packages.inl.fr/debian lenny/ >> /etc/apt/sources.list
#
apt-get update && echo 'y'
#
debconf-set-selections /home/epm/first_installation/preseed/prelude.seed
#
run-parts /home/epm/first_installation/packagelist/*
#
run-parts /home/epm/first_installation/usr/share/siem-live/init
#
echo Script is DONE!
```

---

### Post by mcduck on 2010-04-14
> **davidpbrown said:**
> Not an expert but when in doubt I try adding semi-colons to the end of lines;

However, some scripts seem to work fine without, so I've yet to figure out where they are meant to be used.

Certainly with all the logic forks, like if then else, I've got semi-colons on all lines. The simpler scripts are essentially lists of terminal commands, so maybe limit themselves to reading one line. That is, I'm guessing, maybe it's just bash specific instructions that need them.

Semicolons are just used to separate commands from each other (instead of putting them on separate lines)
[I]
command1
command2
command3[/I]

is the same as 
[I]
command1; command2; command3[/I]

What comes to the original problem this thread is about, could you post the errors you get? That would be really helpful in finding out what's the problem...

---

### Post by Minky2k on 2010-04-14
Just to clarify that I use ubuntu 8.04 and if I paste them in console by hand it seems to work but not with this script.

Problem output:

```
gpg: directory `/root/.gnupg' created
gpg: new configuration file `/root/.gnupg/gpg.conf' created
gpg: WARNING: options in `/root/.gnupg/gpg.conf' are not yet active during this run
gpg: keyring `/root/.gnupg/secring.gpg' created
gpg: keyring `/root/.gnupg/pubring.gpg' created
': No such file or directoryirst_installation/config_chroot_sources_local.gpg
gpg: Total number processed: 0
gpg: can't open `/home/epm/first_installation/config_chroot_sources_packages-inl': No such file or directory
gpg: Total number processed: 0
y
: No such file or directoryirectory /home/epm/first_installation/packagelist/*
```

---

### Post by Minky2k on 2010-04-14
Managed to get the gpg to work by importing manually for the moment. But I still get errors when I run the following scripts, would appreciate any help I could get =)

Main call-script:
```
#!/bin/bash


gpg --import /home/epm/first_installation/config_chroot_sources_local.gpg
gpg --import /home/epm/first_installation/config_chroot_sources_packages-inl-fr.gpg

echo deb http://www.wzdftpd.net/siem-live lenny main >> /etc/apt/sources.list
echo deb http://packages.inl.fr/debian lenny/ >> /etc/apt/sources.list

apt-get update

debconf-set-selections --v /home/epm/first_installation/preseed/prelude.seed

#run-parts --v --list  /home/epm/first_installation/packagelist/

sh /home/epm/first_installation/packagelist/misc.sh
sh /home/epm/first_installation/packagelist/nufw.sh
sh /home/epm/first_installation/packagelist/openvas.sh
sh /home/epm/first_installation/packagelist/prelude.sh
sh /home/epm/first_installation/packagelist/security.sh
sh /home/epm/first_installation/packagelist/snort.sh

#run-parts --v --list  /home/epm/first_installation/usr/share/siem-live/init

sh /home/epm/first_installation/usr/share/siem-live/init/10-rngtools.sh
sh /home/epm/first_installation/usr/share/siem-live/init/20-rsyslog.sh
sh /home/epm/first_installation/usr/share/siem-live/init/50-prelude-database.sh
sh /home/epm/first_installation/usr/share/siem-live/init/50-prewikka-database.sh
sh /home/epm/first_installation/usr/share/siem-live/init/60-prelude-correlator.sh
sh /home/epm/first_installation/usr/share/siem-live/init/70-prelude-notify.sh
sh /home/epm/first_installation/usr/share/siem-live/init/99-first_boot_prelude.sh
sh /home/epm/first_installation/usr/share/siem-live/init/99-first_boot_prewikka.sh
sh /home/epm/first_installation/usr/share/siem-live/init/99-snort.sh

echo Script is DONE!
```

rngtools:
```
#!/bin/sh
echo "[+] Configuring rng-tools "
conf="/etc/default/rng-tools"
cat >> $conf << EOF
#take some entropy from urandom
HRNGDEVICE=/dev/urandom
HRNGDOPTIONS="--fill-watermark=65% --feed-interval=1"
EOF
#if [ "x$target" == "x" ]; then
  invoke-rc.d rng-tools restart
#fi
exit 0

```

syslog:
```
#!/bin/sh
conffile="/etc/rsyslog.conf"
sed -i \
	-e 's/#\(\$ModLoad imudp\)/\1/' \
	-e 's/#\(\$UDPServerRun 514\)/\1/' \
	-e 's/#\(\$ModLoad imtcp\)/\1/' \
	-e 's/#\(\$InputTCPServerRun 514\)/\1/' \
	$conffile
#if [ "x$target" == "x" ]; then
  invoke-rc.d rsyslog restart
#fi
exit 0

```

```
#!/bin/sh
echo "[+] Configuring Prelude Manager and database"
DB="prelude"
USER="prelude"
PASS="Kin6Ead"
conf_dir="/etc/mysql/conf.d"
mem_total=$(free -m | grep Mem | awk '{print $2}')
echo "total memory found: $mem_total"
# take 50% for MySQL
mysql_reserved=$((mem_total * 5 / 10))
echo "allocating $mem_total MB for MySQL"
cat >> $conf_dir/prelude << EOF
[mysqld]
innodb_buffer_pool_size=${mysql_reserved}M
EOF
conffile="/etc/prelude-manager/prelude-manager.conf"
sed -i \
	-e "s/@DBC_TYPE@/mysql/" \
	-e "s/@DBC_HOST@/localhost/" \
	-e "s/@DBC_PORT@/3306/" \
	-e "s/@DBC_NAME@/$DB/" \
	-e "s/@DBC_USER@/$USER/" \
	-e "s/@DBC_PASS@/$PASS/" \
	$conffile
sed -i "s/RUN=no/RUN=yes/" /etc/default/prelude-manager
exit 0

```

```
#!/bin/sh
PRELUDE_DB="prelude"
PRELUDE_USER="prelude"
PRELUDE_PASS="Kin6Ead"
#
PREWIKKA_DB="prewikka"
PREWIKKA_USER="prewikka"
PREWIKKA_PASS="ahZoh8m"
#
conffile="/etc/prewikka/prewikka.conf"
#
# a bit of perl magic for multi-line replace
perl -pi -e \
	"undef $/; s/\[database[^\[]*/[database]\ntype: mysql\nhost: localhost\nuser: $PREWIKKA_USER\npass: $PREWIKKA_PASS\nname: $PREWIKKA_DB\n\n/msg" \
	$conffile
#
perl -pi -e \
	"undef $/; s/\[idmef_database[^\[]*/[idmef_database]\ntype: mysql\nhost: localhost\nuser: $PRELUDE_USER\npass: $PRELUDE_PASS\nname: $PRELUDE_DB\n\n/msg" \
	$conffile
#
#
exit 0

```

```
#!/bin/sh
sed -i "s/RUN=no/RUN=yes/" /etc/default/prelude-correlator
#
exit 0

```

```
#!/bin/sh
sed -i "s/url = http:\/\/localhost:8000/url = http:\/\/localhost\/prelude/g" /etc/prelude-notify/prelude-notify.conf
exit 0

```

```
#!/bin/sh
set -e
#set -x

function wait_regserver
{
    # Wait at most 20 secondes for Prelude registration server to start:
    i=1
    while [ $i -lt 20 ]; do
        if netstat -lnpt |grep -q :5553; then
            return 0
        fi
        sleep 1
        i=$(($i + 1))
    done

    exit 1
}

#/sbin/splashy_update "TEXT configuring first boot parameters (Prelude manager)" ||:

echo "----------------------------------------------------"
echo "   Configuring first boot parameters (prelude manager)"
echo "----------------------------------------------------"

DB="prelude"
USER="prelude"
PASS="Kin6Ead"


#/sbin/splashy_update "TEXT creating prelude database" ||:
echo "[+] creating prelude database"
echo "CREATE DATABASE $DB;" | mysql -uroot
echo "GRANT ALL PRIVILEGES ON $DB.* TO '$USER'@'localhost' IDENTIFIED BY '$PASS';" | mysql -uroot

mysql -u$USER -p$PASS $DB < /usr/share/dbconfig-common/data/prelude-manager/install/mysql


echo "[+] setting prelude-manager bind address to 0.0.0.0"
sed -i 's/^listen.*/listen = 0.0.0.0/' /etc/prelude-manager/prelude-manager.conf


echo "[+] (re-)starting prelude manager"
/etc/init.d/prelude-manager start ||:

## LML
#/sbin/splashy_update "TEXT creating and registering prelude-lml profile" ||:
echo "[+] creating and registering prelude-lml profile"

killall prelude-admin &>/dev/null ||:
(/usr/local/sbin/prelude-simple-regserver blah ||: ) &

echo "[+] waiting 10 seconds for registration-server to start"
wait_regserver

prelude-admin register prelude-lml "idmef:w" 127.0.0.1 --uid 0 --gid 0 --passwd blah ||:

echo "[+] (re-)starting prelude lml"
/etc/init.d/prelude-lml restart ||:

## Correlator
#/sbin/splashy_update "TEXT creating and registering prelude-correlator profile" ||:
echo "[+] creating and registering prelude-correlator profile"

killall prelude-admin &>/dev/null ||:
(/usr/local/sbin/prelude-simple-regserver blah ||: ) &

echo "[+] waiting 10 seconds for registration-server to start"
wait_regserver

prelude-admin register prelude-correlator "idmef:rw" 127.0.0.1 --uid prelude-correlator --gid prelude-correlator --passwd blah ||:

echo "[+] (re-)starting prelude correlator"
(/etc/init.d/prelude-correlator restart ||: ) &

## Prelude Notify
#/sbin/splashy_update "TEXT creating and registering prelude-notify profile" ||:
echo "[+] creating and registering prelude-correlator profile"

killall prelude-admin &>/dev/null ||:
(/usr/local/sbin/prelude-simple-regserver blah ||: ) &

echo "[+] waiting 10 seconds for registration-server to start"
wait_regserver

prelude-admin register prelude-notify "idmef:rw" 127.0.0.1 --uid user --gid user --passwd blah ||:

echo "[+] prelude-notify registered"



exit 0

```

```
#!/bin/sh
set -e
#set -x

echo "----------------------------------------------------"
echo "   Configuring first boot parameters (prewikka)"
echo "----------------------------------------------------"

PRELUDE_DB="prelude"
PRELUDE_USER="prelude"
PRELUDE_PASS="Kin6Ead"

PREWIKKA_DB="prewikka"
PREWIKKA_USER="prewikka"
PREWIKKA_PASS="ahZoh8m"

echo "[+] creating prewikka database"
echo "CREATE DATABASE $PREWIKKA_DB;" | mysql -uroot
echo "GRANT ALL PRIVILEGES ON $PREWIKKA_DB.* TO '$PREWIKKA_USER'@'localhost' IDENTIFIED BY '$PREWIKKA_PASS';" | mysql -uroot

mysql -u$PREWIKKA_USER -p$PREWIKKA_PASS $PREWIKKA_DB < /usr/share/dbconfig-common/data/prewikka/install/mysql

echo "[+] configuring apache2"
install -m0644 /usr/share/siem-live/conf/apache2_site_config /etc/apache2/sites-available/prewikka

a2dissite 000-default ||:
a2ensite prewikka

chgrp www-data /etc/prewikka/prewikka.conf
chmod 0640 /etc/prewikka/prewikka.conf

exit 0

```

```
#!/bin/sh
set -e
#set -x

function wait_regserver
{
    # Wait at most 20 secondes for Prelude registration server to start:
    i=1
    while [ $i -lt 20 ]; do
        if netstat -lnpt |grep -q :5553; then
            return 0
        fi
        sleep 1
        i=$(($i + 1))
    done

    exit 1
}

#/sbin/splashy_update "TEXT configuring and creating profile for snort" ||:

echo "----------------------------------------------------"
echo "   Configuring first boot parameters (snort)"
echo "----------------------------------------------------"

CONF="/etc/snort/snort.conf"

sed -i 's/^# output alert_prelude$/output alert_prelude/' $CONF

echo "[+] creating and registering snort profile"

killall prelude-admin &>/dev/null ||:
(/usr/local/sbin/prelude-simple-regserver blah ||: ) &

echo "[+] waiting 10 seconds for registration-server to start"
wait_regserver

prelude-admin register snort "idmef:w" 127.0.0.1 --uid snort --gid snort --passwd blah ||:

echo "[+] (re-)starting snort"
(/etc/init.d/snort restart ||:) &


exit 0

```

---

