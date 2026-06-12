---
title: "Sharing MYSQL tables between Ubuntu/Windows"
date: 2010-02-21
forum: General Help
---

### Post by HuckBerry on 2010-02-21
I am currently setting up a box as a dual-boot.
/dev/sda1 is Windows 7 (bootloader)
/dev/sda2 is Windows 7
/dev/sda3 is Shared NTFS partition
/dev/sda4 is Ubuntu 9.10
/dev/sda5 is Linux-swap

My question is, is it possible to place the Data directory for Mysql Server on the shared NTFS partition so that I can boot into either OS and have the server + data available. This setup has worked beautifully for Apache using symlinks to the Shared partition, however mysql is much more complicated system, involving disk writes and multiple simultaneous disk reads.

So far I have /dev/sda3 mounted as /media/Shared with root drwxrwxrwx permissions via a line in fstab: 
/dev/sda3    /media/Shared    ntfs    auto,noexec,rw,dmask=0000,fmask=0000

The Windows version of mysql is already configured as having E:\MySqlData as the DataDir and is functioning, I just edited the linux my.cnf to use /media/Shared/MySqlData as the datadir however it fails to restart on /etc/init.d/mysql restart. The last few lines of syslog show some issues with permissions:
```

mysqld_safe: Starting mysqld daemon with databases from /media/Shared/MySQLData
kernel: [ 7208.669710] type=1503 audit(1266778344.312:85): operation="open" pid=6441 parent=6333 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
mysqld: 100221 13:52:24 [Warning] Can't create test file /media/Shared/MySQLData/UbuntuDesktop.lower-test
mysqld: 100221 13:52:24 [Warning] Can't create test file /media/Shared/MySQLData/UbuntuDesktop.lower-test
...
...
mysqld: 100221 13:52:24  InnoDB: Operating system error number 13 in a file operation.
mysqld: InnoDB: The error means mysqld does not have the access rights to
mysqld: InnoDB: the directory.
mysqld: InnoDB: File name ./ibdata1
mysqld: InnoDB: File operation call: 'open'.
mysqld: InnoDB: Cannot continue operation.

```Permissions for /media/Shared and subdir/files are root [d]rwxrwxrwx so I'm not entirely sure why mysql is being denied writes. Any Ideas?

---

### Post by DaithiF on 2010-02-21
probably apparmor -- preventing mysql from accessing files in this 'unexpected' location.
you can set apparmor to complain mode rather than blocking mode for mysqld, like so...
```
sudo aa-complain /usr/sbin/mysqld
```
then restart mysql and see if it runs ok

---

### Post by HuckBerry on 2010-02-21
I tried aa-comlain on mysql and mysqld_safe however no dice. Same set of errors -- the full syslog is below. I copied the entire /var/lib/mysql/mysql folder (since the one on the shared directory was the windows one) but again no dice.

```

kernel: [34600.968412] type=1503 audit(1266805736.612:177): operation="open" pid=9390 parent=9389 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
kernel: [34600.984209] type=1503 audit(1266805736.628:178): operation="open" pid=9399 parent=9398 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
kernel: [34601.035807] type=1503 audit(1266805736.676:179): operation="open" pid=9414 parent=9413 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
kernel: [34601.090088] type=1503 audit(1266805736.732:180): operation="open" pid=9435 parent=9434 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
mysqld_safe: Starting mysqld daemon with databases from /media/Shared/MySQLData
kernel: [34601.249546] type=1503 audit(1266805736.892:181): operation="open" pid=9549 parent=9441 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
kernel: [34601.255644] type=1503 audit(1266805736.896:182): operation="mknod" pid=9549 parent=9441 profile="/usr/sbin/mysqld" requested_mask="w::" denied_mask="w::" fsuid=0 ouid=0 name="/media/Shared/MySQLData/UbuntuDesktop.lower-test"
kernel: [34601.255825] type=1503 audit(1266805736.896:183): operation="mknod" pid=9549 parent=9441 profile="/usr/sbin/mysqld" requested_mask="w::" denied_mask="w::" fsuid=0 ouid=0 name="/media/Shared/MySQLData/UbuntuDesktop.lower-test"
mysqld: 100221 21:28:56 [Warning] Can't create test file /media/Shared/MySQLData/UbuntuDesktop.lower-test
mysqld: 100221 21:28:56 [Warning] Can't create test file /media/Shared/MySQLData/UbuntuDesktop.lower-test
mysqld: 100221 21:28:56 [Note] Plugin 'FEDERATED' is disabled.
kernel: [34601.260409] type=1503 audit(1266805736.904:184): operation="open" pid=9549 parent=9441 profile="/usr/sbin/mysqld" requested_mask="::r" denied_mask="::r" fsuid=115 ouid=0 name="/media/Shared/MySQLData/mysql/plugin.frm"
mysqld: #007/usr/sbin/mysqld: Can't find file: './mysql/plugin.frm' (errno: 13)
mysqld: 100221 21:28:56 [ERROR] Can't open the mysql.plugin table. Please run mysql_upgrade to create it.
mysqld: 100221 21:28:56  InnoDB: Operating system error number 13 in a file operation.
mysqld: InnoDB: The error means mysqld does not have the access rights to
mysqld: InnoDB: the directory.
mysqld: InnoDB: File name ./ibdata1
mysqld: InnoDB: File operation call: 'open'.
mysqld: InnoDB: Cannot continue operation.
kernel: [34601.288356] type=1503 audit(1266805736.932:185): operation="open" pid=9549 parent=9441 profile="/usr/sbin/mysqld" requested_mask="::rw" denied_mask="::rw" fsuid=115 ouid=0 name="/media/Shared/MySQLData/ibdata1"
mysqld_safe: mysqld from pid file /var/run/mysqld/mysqld.pid ended
kernel: [34602.119322] type=1503 audit(1266805737.760:186): operation="open" pid=9561 parent=9560 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
kernel: [34606.230800] __ratelimit: 9 callbacks suppressed
kernel: [34606.230808] type=1503 audit(1266805741.872:190): operation="open" pid=9601 parent=9600 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
kernel: [34607.257375] type=1503 audit(1266805742.900:191): operation="open" pid=9611 parent=9610 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
kernel: [34608.302150] type=1503 audit(1266805743.944:192): operation="open" pid=9621 parent=9620 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
kernel: [34609.326547] type=1503 audit(1266805744.968:193): operation="open" pid=9631 parent=9630 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
kernel: [34610.355936] type=1503 audit(1266805745.996:194): operation="open" pid=9641 parent=9640 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
kernel: [34611.398498] type=1503 audit(1266805747.040:195): operation="open" pid=9651 parent=9650 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
kernel: [34612.427020] type=1503 audit(1266805748.069:196): operation="open" pid=9663 parent=9662 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
kernel: [34613.472579] type=1503 audit(1266805749.117:197): operation="open" pid=9673 parent=9672 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
kernel: [34614.500917] type=1503 audit(1266805750.144:198): operation="open" pid=9683 parent=9682 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
kernel: [34615.527727] type=1503 audit(1266805751.168:199): operation="open" pid=9693 parent=9692 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
kernel: [34615.554399] type=1503 audit(1266805751.196:200): operation="open" pid=9702 parent=9701 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
/etc/init.d/mysql[9709]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
/etc/init.d/mysql[9709]: #007/usr/bin/mysqladmin: connect to server at 'localhost' failed
/etc/init.d/mysql[9709]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
/etc/init.d/mysql[9709]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
/etc/init.d/mysql[9709]: 

```

---

### Post by DaithiF on 2010-02-22
those kernel messages look like they are apparmor related to me.
Refer to the documentation here: [https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)
for more details on disabling apparmor profiles.

---

### Post by HuckBerry on 2010-02-22
Disabling apparmor entirely (via uninstalling it) did indeed allow mysql to load fully. I am going to switch to windows to see if I can do the same there. Once both systems load mysql correctly I will reinstall apparmor (i left all the profiles in place when I took it out) and tweak it to allow /media/Shared/MySQLData.

Will report back with results.

//EDIT
-Had to set Windows to use MYISAM by default by editing my.ini:  default-storage-engine=MYISAM
-Had to convert all tables already created with INNODB using: ALTER TABLE <name> ENGINGE=MYISAM; (This must be done from windows)
-After reinstalling apparmor had to execute the following to Disable the mysql profile:
sudo ln -s /etc/apparmor.d/usr.sbin.mysqld /etc/apparmor.d/disable/
sudo apparmor_parser -R /etc/apparmor.d/usr.sbin.mysqld

---

### Post by Ignatius Reilly on 2010-03-11
Ubuntu newbie. I struggled on pointing a MySQL datadir to a mounted FAT32 volume.  
 
I tried to edit the /etc/apparmor.d/usr.sbin.mysqld configurations to point to the mounted location, to no avail. 
Changing the umask mount parameter for the fat volume was also without effect. 
So I disabled apparmor for mysqld, as suggested in this thread. 
 
... Now this alone did not do the trick. 
I found that the problem lied in that I had declared the location on the mounted volume directly in the my.cnf datadir. 
After creating a symlink from /var/lib/mysql to the mounted datadir, I could start the mysqld server: 
```
sudo ln -s /opt/data/mysql5 /var/lib/mysql/mysql5
```(permissions) 
Note: I tried without success to chown the symlink to mysql:mysql, still it worked, somewhat mysteriously (I initially assumed that the datadir location has to be owned by the mysql user, but it doesn't seem to be the case). 
 
Mounting option for the vfat volume are: 
```
rw,sync,utf8,uid=1000,umask=0000,shortname=mixed 
```Hope this will help.

---

### Post by HuckBerry on 2010-03-11
chowning a symlink wont have any effect on the symlink because symlinks use the permissions of their targets. Since your symlink points to a filesystem that doesn't support ext permissions it will inherit the permissions of the device (as defined either on the command line or in fstab)

As far as the mysql user owning the datadir, I'm not 100% sure it is needed. I found many of the pre-existing directories and files in my mysql dir were owned by root:root (-rwx-rw----). However I had only a root (mysql)user on my server, non-root mysql accounts may use mysql:mysql instead.

---

### Post by rveloso on 2010-10-11
u dont need to remove apparmor, just edit /etc/apparmor.d/tunables and add the new dir there as well

---

