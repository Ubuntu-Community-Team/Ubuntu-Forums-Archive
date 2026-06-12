---
title: "Lost Root Privileges in phpmyadmin"
date: 2010-10-30
forum: General Help
---

### Post by carsonrose on 2010-10-30
Ive been messing with this for the better part or three days now... 

Ive done something, Im not sure what...... I was trying to backup my mysql DB so I can reformat that server and install different server OS, then reinstall mysql and restore the DB...

Well, somewhere in this mess I did something and now I get 
**DBI connect failed : Access denied for user ''@'localhost' to database 'mysql'**

CONSTANTLY! 

I cant see any of my SQL DB's anymore... I just need to get the privileges back that Im missing, back up these DB's and get on with this already!

Any ideas?

---

### Post by gerahmartinez on 2010-10-30
Try reseting your root password, check out this link.

[http://forums.mysql.com/read.php?11,34014,46593#msg-46593]("http://forums.mysql.com/read.php?11,34014,46593#msg-46593")

---

### Post by v1ad on 2010-10-30
mysql -u root  ?? if you have a root password

mysql -u root -p

---

### Post by carsonrose on 2010-10-31
> **v1ad said:**
> mysql -u root  ?? if you have a root password

mysql -u root -p


Here is what I get:
```
[root@cra-c1 etc]# mysql -u root
Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MariaDB connection id is 3420
Server version: 5.1.47-MariaDB Source distribution

Copyright (c) 2000, 2010, Oracle and/or its affiliates. All rights reserved.
This software comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to modify and redistribute it under the GPL v2 license

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

MariaDB [(none)]> 
```

Notice, Im not in a database above... even thought Im root......

When I try to view my databases:
```
MariaDB [(none)]> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| test               |
+--------------------+
2 rows in set (0.00 sec)

MariaDB [(none)]> 
```

I dont know what that Maria crap is, I dont know how it got there... and more importantly, I cant see my DBs...

Ive tried all the posts, without luck... there is always some caveat that prevents me from completing the task...

---

### Post by carsonrose on 2010-10-31
> **gerahmartinez said:**
> Try reseting your root password, check out this link.

[http://forums.mysql.com/read.php?11,34014,46593#msg-46593](http://forums.mysql.com/read.php?11,34014,46593#msg-46593)
```


[root@cra-c1 ~]# mysql --skip-grant-tables
mysql: unknown option '--skip-grant-tables'
[root@cra-c1 ~]# mysqld --skip-grant-tables
-bash: mysqld: command not found
[root@cra-c1 ~]# pidof mysqld
5813
[root@cra-c1 ~]# mysql
Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MariaDB connection id is 2933
Server version: 5.1.47-MariaDB Source distribution

Copyright (c) 2000, 2010, Oracle and/or its affiliates. All rights reserved.
This software comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to modify and redistribute it under the GPL v2 license

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

MariaDB [(none)]> mysql;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'mysql' at line 1
MariaDB [(none)]> show databases
    -> ^C
    -> 
    -> 
    -> exit
    -> ^CCtrl-C -- exit!
Aborted
[root@cra-c1 ~]# ^C
[root@cra-c1 ~]# 
[root@cra-c1 ~]# 
[root@cra-c1 ~]# mysql
Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MariaDB connection id is 3135
Server version: 5.1.47-MariaDB Source distribution

Copyright (c) 2000, 2010, Oracle and/or its affiliates. All rights reserved.
This software comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to modify and redistribute it under the GPL v2 license

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

MariaDB [(none)]> mysql;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'mysql' at line 1
MariaDB [(none)]> mysql
    -> 
    -> 
    -> 
    -> quit
    -> Ctrl-C -- exit!
Aborted
[root@cra-c1 ~]# mysqld_safe --skip-grant-tables &
[1] 27533
[root@cra-c1 ~]# 101030 23:39:33 mysqld_safe Logging to '/var/log/mysqld.log'.
101030 23:39:33 mysqld_safe A mysqld process already exists

[1]+  Exit 1                  mysqld_safe --skip-grant-tables
[root@cra-c1 ~]# cd /etc/my.cnf 
anaconda-ks.cfg              .gconfd/                     .lesshst                     .serverauth.6444
.bash_history                .gnome/                      .mc/                         .ssh/
.bash_logout                 .gnome2/                     .metacity/                   .tcshrc
.bash_profile                .gnome2_private/             .mysql_history               .thumbnails/
.bashrc                      .gnupg/                      .nautilus/                   .Trash/
.cshrc                       .gstreamer-0.10/             osdial-split.sql             .viminfo
Desktop/                     .gtkrc-1.2-gnome2            .redhat/                     .vnc/
.eggcups/                    .ICEauthority                restore_root_privileges.sql  .Xauthority
.elinks/                     install.log                  .rnd                         
.gconf/                      install.log.syslog           .serverauth.4167             
[root@cra-c1 ~]# cd /etc/
[root@cra-c1 etc]# ls
acpi                   dhcp6c.conf           inputrc         Muttrc              purple             shadow
adjtime                DIR_COLORS            iproute2        Muttrc.local        quotagrpadmins     shadow-
aliases                DIR_COLORS.xterm      isdn            my.cnf              quotatab           shells
aliases.db             dnsmasq.conf          issue           netplug             racoon             skel
alsa                   dumpdates             issue.net       netplug.d           rc                 slrn.rc
alternatives           environment           issue.rpmnew    NetworkManager      rc0.d              smart
anacrontab             esd.conf              java            nscd.conf           rc1.d              smartd.conf
apt                    exports               jvm             nsswitch.conf       rc2.d              smrsh
asterisk               fb.modes              jvm-commmon     ntp                 rc3.d              sound
at.deny                filesystems           jwhois.conf     ntp.conf            rc4.d              ssh
audisp                 firmware              krb5.conf       odbc.ini            rc5.d              stunnel
audit                  fonts                 ldap.conf       odbcinst.ini        rc6.d              sudoers
autofs_ldap_auth.conf  foomatic              ld.so.cache     oddjob              rc.d               sysconfig
auto.master            fstab                 ld.so.conf      oddjobd.conf        rc.local           sysctl.conf
auto.misc              gconf                 ld.so.conf.d    oddjobd.conf.d      rc.sysinit         syslog.conf
auto.net               gcrypt                lftp.conf       openldap            readahead.d        tcsd.conf
auto.smb               gdm                   libaudit.conf   openvpn             reader.conf        termcap
avahi                  ghostscript           libuser.conf    opt                 reader.conf.d      udev
bashrc                 gnome-vfs-2.0         localtime       osdial.conf         redhat-lsb         updatedb.conf
blkid                  gnome-vfs-mime-magic  login.defs      osdial.conf.rpmnew  redhat-release     usermin
bluetooth              gpm-root.conf         logrotate.conf  pam.d               request-key.conf   vimrc
bonobo-activation      gre.d                 logrotate.d     pam_pkcs11          resolv.conf        virc
capi.conf              group                 logwatch        pam_smb.conf        resolv.conf.bak    wanpipe
cdrecord.conf          group-                lsb-release.d   pango               rhgb               warnquota.conf
cipe                   grub.conf             lvm             passwd              rmt                webmin
conman.conf            gshadow               mail            passwd-             rpc                wgetrc
cron.d                 gshadow-              mailcap         pcmcia              rpm                wpa_supplicant
cron.daily             gssapi_mech.conf      mail.rc         pear.conf           rwtab              wvdial.conf
cron.deny              gtk                   makedev.d       php.d               rwtab.d            X11
cron.hourly            gtk-2.0               man.config      php.ini             samba              xdg
cron.monthly           hal                   maven           php.ini.rpmnew      sangoma_mgd.conf   xinetd.conf
crontab                host.conf             mc              pinforc             sasl2              xinetd.d
cron.weekly            HOSTNAME              mgetty+sendfax  pki                 screenrc           xml
csh.cshrc              hosts                 mime.types      pm                  scrollkeeper.conf  xrdp
csh.login              hosts.allow           minicom.users   ppp                 scsi_id.config     yp.conf
cups                   hosts.deny            mke2fs.conf     prelink.cache       securetty          yum
dahdi                  hotplug               modprobe.conf   prelink.conf        security           yum.conf
dbus-1                 httpd                 modprobe.d      prelink.conf.d      selinux            yum.repos.d
default                idmapd.conf           motd            printcap            services           zaptel.bak
depmod.d               init.d                mtab            profile             sestatus.conf
desktop-profiles       initlog.conf          mtools.conf     profile.d           setuptool.d
dev.d                  inittab               multipath.conf  protocols           sgml
[root@cra-c1 etc]# vim  mt
mtab         mtools.conf  
[root@cra-c1 etc]# vim  mt
mtab         mtools.conf  
[root@cra-c1 etc]# vim my.cnf 
[root@cra-c1 etc]# mysql -u root
Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MariaDB connection id is 3420
Server version: 5.1.47-MariaDB Source distribution

Copyright (c) 2000, 2010, Oracle and/or its affiliates. All rights reserved.
This software comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to modify and redistribute it under the GPL v2 license

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

MariaDB [(none)]> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| test               |
+--------------------+
2 rows in set (0.00 sec)

MariaDB [(none)]> quit
Bye
[root@cra-c1 etc]# /etc/init.d/mysqld stop
Stopping MySQL:                                            [  OK  ]
[root@cra-c1 etc]# mysqld_safe --skip-grant-tables &
[1] 29950
[root@cra-c1 etc]# 101030 23:59:47 mysqld_safe Logging to '/var/log/mysqld.log'.
101030 23:59:47 mysqld_safe Starting mysqld daemon with databases from /var/lib/mysql

[root@cra-c1 etc]# mysql -u root mysql 
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MariaDB connection id is 27
Server version: 5.1.47-MariaDB Source distribution

Copyright (c) 2000, 2010, Oracle and/or its affiliates. All rights reserved.
This software comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to modify and redistribute it under the GPL v2 license

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

MariaDB [mysql]> UPDATE user SET Password=PASSWORD('trolly') where USER='root'; 
Query OK, 0 rows affected (0.00 sec)
Rows matched: 3  Changed: 0  Warnings: 0

MariaDB [mysql]> FLUSH PRIVILEGES; 
Query OK, 0 rows affected (0.00 sec)

MariaDB [mysql]> quit
Bye
[root@cra-c1 etc]# /etc/init.d/mysqld stop
101031 00:02:31 mysqld_safe mysqld from pid file /var/run/mysqld/mysqld.pid ended
Stopping MySQL:                                            [  OK  ]
[1]+  Done                    mysqld_safe --skip-grant-tables
[root@cra-c1 etc]# /etc/init.d/mysqld start
Starting MySQL:                                            [  OK  ]
[root@cra-c1 etc]# mysql -u root -p 
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
[root@cra-c1 etc]# mysql -u root -p 
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
[root@cra-c1 etc]# mysql -u root -p 
Enter password: 
Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MariaDB connection id is 82
Server version: 5.1.47-MariaDB Source distribution

Copyright (c) 2000, 2010, Oracle and/or its affiliates. All rights reserved.
This software comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to modify and redistribute it under the GPL v2 license

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

MariaDB [(none)]> quit
Bye
"
```

---

### Post by carsonrose on 2010-10-31
Really, I could care less about using this system after this, I just need to back up the database and restore it on a different computer...  I am installing a new dialer...

---

