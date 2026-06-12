---
title: "Mounting a disk in ./usr"
date: 2011-09-21
forum: General Help
---

### Post by johandsom3 on 2011-09-21
Hello fellow ubuntu users.

I'm pretty new to using ubuntu, and my boss told me to mount a partition in /usr.

I have tried two different methods and both of them have failed.
Link: [http://www.unix.com/solaris/97072-mount-usr-separate-filesystem.html](http://www.unix.com/solaris/97072-mount-usr-separate-filesystem.html)

When i mount my partition into /usr i cant seem to get permission to use sudo and such, even though they are supposed to have the same files within.

Does anyone have a solution to this? You may have noticed that my writing skills in english isn't that good, but I can read english very well,.

---

### Post by WorMzy on 2011-09-21
How did you copy files from the old partition to the new partition? If you used cp, make sure to use the -p flag so that permissions are preserved, otherwise all the files will change to root ownership with the default umask.

Not sure whether file permissions would be maintained if you copied using a graphical file manager in gksu mode.

---

### Post by lordbux on 2011-09-21
> **johandsom3 said:**
> Hello fellow ubuntu users.

I'm pretty new to using ubuntu, and my boss told me to mount a partition in /usr.

I have tried two different methods and both of them have failed.
Link: [http://www.unix.com/solaris/97072-mount-usr-separate-filesystem.html](http://www.unix.com/solaris/97072-mount-usr-separate-filesystem.html)

When i mount my partition into /usr i cant seem to get permission to use sudo and such, even though they are supposed to have the same files within.

Does anyone have a solution to this? You may have noticed that my writing skills in english isn't that good, but I can read english very well,.

to mount it to /usr every time the computer boots with full functionality

just open /etc/fstab/ as super user or use
```
sudo gedit /usr/
```

then just add the following info on new line

```
<device path>  /usr <format like fat32 ..etc> errors=remount-ro  0       1
``` 
[B]
DONOT put the < or >
MAKE SURE you REMOVE other line that specify to same device[/B]

save the file

DONOT RESTART OR RUN MOUND COMMAND NOW
then copy everything into this drive from /usr

delete everything in /usr

 restart system :guitar:

hope this works

---

### Post by johandsom3 on 2011-09-22
But how do i copy the files that are inside "/usr"?

you said i shouldnt mount anything, but i'll guess that it would be much easier if i could mount to "/mnt" and then copy the files with SFTP

is this possible?

edit: tried using sftp, i couldn't make it work:p

---

### Post by WorMzy on 2011-09-22
You can't copy files that are in /usr if you mount something over the top of it. Until you've copied everything over, mount the new partition somewhere like /media/usr or /mnt

Why are you trying to use SFTP? That's for accessing files on a remote server.

---

### Post by johandsom3 on 2011-09-22
> **WorMzy said:**
> You can't copy files that are in /usr if you mount something over the top of it. Until you've copied everything over, mount the new partition somewhere like /media/usr or /mnt

Why are you trying to use SFTP? That's for accessing files on a remote server.

I wasnt planning to mount anything on top of it. I ment mounting in /mnt... Anyways, i gave it a try... here is what i did:

Sudo nano -w /etc/fstab
     /dev/sdb3  /usr ext2 errors=remount-ro  0       1
sudo mount /dev/sdb3 /mnt
sudo cp -r -p /usr/* /mnt
that worked ( checked if the files were there)
Then i deleted everything in /usr and umounted /mnt.
tried a reboot, but since i deleted the /usr files, i cannot do that, so i did a hard shutdown (?) When the machine booted, i got presented with a not so welcoming text :(

[IMG]http://i52.tinypic.com/2jd13bs.png[/IMG]

Why did i try SFTP? A friend told me so.

edit: well the machine actually works... with usr mounted, but it says "File not found" on every startup.

---

### Post by WorMzy on 2011-09-22
Well, looks like you did everything correctly (apart from setting fs_passno to 1 for the /usr mount, use 2 for any linux partitions that aren't the root partition)

Are you saying that you can still boot, even though it's saying "command not found"? If so, check your log files: /var/log/error.log, /var/log/daemon.log, etc. and see if there's any hints as to what's not found.

If they offer no insight, try booting without "quiet" on the kernel command line. [This]("https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot") should explain how to do that.

---

### Post by johandsom3 on 2011-09-22
Yup, i can still boot... The "file not found" commands stays there 3 seconds, then i get transfered to my login screen.


Daemon error log.
> Sep 22 10:24:55 webserver init: ssh main process (596) terminated with status 25                                                 5
Sep 22 10:24:55 webserver init: apport pre-start process (704) terminated with s                                                 tatus 1
Sep 22 10:24:55 webserver init: apport post-stop process (722) terminated with s                                                 tatus 1
Sep 22 10:24:57 webserver /etc/mysql/debian-start[831]: Upgrading MySQL tables i                                                 f necessary.
Sep 22 10:24:57 webserver /etc/mysql/debian-start[834]: /usr/bin/mysql_upgrade:                                                  the '--basedir' option is always ignored
Sep 22 10:24:57 webserver /etc/mysql/debian-start[834]: Looking for 'mysql' as:                                                  /usr/bin/mysql
Sep 22 10:24:57 webserver /etc/mysql/debian-start[834]: Looking for 'mysqlcheck'                                                  as: /usr/bin/mysqlcheck
Sep 22 10:24:57 webserver /etc/mysql/debian-start[834]: Running 'mysqlcheck' wit                                                 h connection arguments: '--port=3306' '--socket=/var/run/mysqld/mysqld.sock' '--                                                 host=localhost' '--socket=/var/run/mysqld/mysqld.sock' '--host=localhost' '--soc                                                 ket=/var/run/mysqld/mysqld.sock'
Sep 22 10:24:57 webserver /etc/mysql/debian-start[834]: Running 'mysqlcheck' wit                                                 h connection arguments: '--port=3306' '--socket=/var/run/mysqld/mysqld.sock' '--                                                 host=localhost' '--socket=/var/run/mysqld/mysqld.sock' '--host=localhost' '--soc                                                 ket=/var/run/mysqld/mysqld.sock'
Sep 22 10:24:57 webserver /etc/mysql/debian-start[834]: mysql.columns_priv                                                                                  OK
Sep 22 10:24:57 webserver /etc/mysql/debian-start[834]: mysql.db                                                                                            OK
Sep 22 10:24:57 webserver /etc/mysql/debian-start[834]: mysql.event                                                                                         OK
Sep 22 10:24:57 webserver /etc/mysql/debian-start[834]: mysql.func                                                                                          OK
Sep 22 10:24:57 webserver /etc/mysql/debian-start[834]: mysql.general_log
Sep 22 10:24:57 webserver /etc/mysql/debian-start[834]: Error    : You can't use                                                  locks with log tables.
Sep 22 10:24:57 webserver /etc/mysql/debian-start[834]: status   : OK
Sep 22 10:24:57 webserver /etc/mysql/debian-start[834]: mysql.help_category                                                                                 OK
Sep 22 10:24:57 webserver /etc/mysql/debian-start[834]: mysql.help_keyword                                                                                  OK
Sep 22 10:24:57 webserver /etc/mysql/debian-start[834]: mysql.help_relation                                                                                 OK
Sep 22 10:24:57 webserver /etc/mysql/debian-start[834]: mysql.help_topic                                                                                    OK
Sep 22 10:24:57 webserver /etc/mysql/debian-start[834]: mysql.host                                                                                          OK
Sep 22 10:24:57 webserver /etc/mysql/debian-start[834]: mysql.ndb_binlog_index                                                                              OK
Sep 22 10:24:57 webserver /etc/mysql/debian-start[834]: mysql.plugin                                                                                        OK
Sep 22 10:24:57 webserver /etc/mysql/debian-start[834]: mysql.proc                                                                                          OK
Sep 22 10:24:57 webserver /etc/mysql/debian-start[834]: mysql.procs_priv                                                                                    OK
Sep 22 10:24:57 webserver /etc/mysql/debian-start[834]: mysql.servers                                                                                       OK
Sep 22 10:24:57 webserver /etc/mysql/debian-start[834]: mysql.slow_log
Sep 22 10:24:57 webserver /etc/mysql/debian-start[834]: Error    : You can't use                                                  locks with log tables.
Sep 22 10:24:57 webserver /etc/mysql/debian-start[834]: status   : OK
Sep 22 10:24:57 webserver /etc/mysql/debian-start[834]: mysql.tables_priv                                                                                   OK
Sep 22 10:24:57 webserver /etc/mysql/debian-start[834]: mysql.time_zone                                                                                     OK
Sep 22 10:24:57 webserver /etc/mysql/debian-start[834]: mysql.time_zone_leap_sec                                                 ond                        OK
Sep 22 10:24:57 webserver /etc/mysql/debian-start[834]: mysql.time_zone_name                                                                                OK
Sep 22 10:24:57 webserver /etc/mysql/debian-start[834]: mysql.time_zone_transiti                                                 on                         OK
Sep 22 10:24:57 webserver /etc/mysql/debian-start[834]: mysql.time_zone_transiti                                                 on_type                    OK
Sep 22 10:24:57 webserver /etc/mysql/debian-start[834]: mysql.user                                                                                          OK
Sep 22 10:24:57 webserver /etc/mysql/debian-start[834]: Running 'mysql_fix_privi                                                 lege_tables'...
Sep 22 10:24:57 webserver /etc/mysql/debian-start[834]: OK
Sep 22 10:24:57 webserver /etc/mysql/debian-start[851]: Checking for insecure ro                                                 ot accounts.
Sep 22 10:24:57 webserver /etc/mysql/debian-start[855]: Triggering myisam-recove                                                 r for all MyISAM tables
Sep 22 10:24:59 webserver ntpdate[686]: no server suitable for synchronization f                                                 ound
Sep 22 12:32:27 webserver init: apport pre-start process (705) terminated with s                                                 tatus 1
Sep 22 12:32:27 webserver init: apport post-stop process (717) terminated with s                                                 tatus 1
Sep 22 12:32:28 webserver /etc/mysql/debian-start[816]: Upgrading MySQL tables i                                                 f necessary.
Sep 22 12:32:28 webserver /etc/mysql/debian-start[819]: /usr/bin/mysql_upgrade:                                                  the '--basedir' option is always ignored
Sep 22 12:32:28 webserver /etc/mysql/debian-start[819]: Looking for 'mysql' as:                                                  /usr/bin/mysql
Sep 22 12:32:28 webserver /etc/mysql/debian-start[819]: Looking for 'mysqlcheck'                                                  as: /usr/bin/mysqlcheck
Sep 22 12:32:28 webserver /etc/mysql/debian-start[819]: This installation of MyS                                                 QL is already upgraded to 5.1.41, use --force if you still need to run mysql_upg                                                 rade
Sep 22 12:32:28 webserver /etc/mysql/debian-start[826]: Checking for insecure ro                                                 ot accounts.
Sep 22 12:32:28 webserver /etc/mysql/debian-start[830]: Triggering myisam-recove                                                 r for all MyISAM tables
Sep 22 12:54:05 webserver init: ssh main process (627) terminated with status 25                                                 5
Sep 22 12:54:05 webserver init: apport pre-start process (716) terminated with s                                                 tatus 1
Sep 22 12:54:05 webserver init: apport post-stop process (735) terminated with s                                                 tatus 1
Sep 22 12:54:06 webserver /etc/mysql/debian-start[827]: Upgrading MySQL tables i                                                 f necessary.
Sep 22 12:54:06 webserver /etc/mysql/debian-start[830]: /usr/bin/mysql_upgrade:                                                  the '--basedir' option is always ignored
Sep 22 12:54:06 webserver /etc/mysql/debian-start[830]: Looking for 'mysql' as:                                                  /usr/bin/mysql
Sep 22 12:54:06 webserver /etc/mysql/debian-start[830]: Looking for 'mysqlcheck'                                                  as: /usr/bin/mysqlcheck
Sep 22 12:54:06 webserver /etc/mysql/debian-start[830]: This installation of MyS                                                 QL is already upgraded to 5.1.41, use --force if you still need to run mysql_upg                                                 rade
Sep 22 12:54:06 webserver /etc/mysql/debian-start[837]: Checking for insecure ro                                                 ot accounts.
Sep 22 12:54:06 webserver /etc/mysql/debian-start[841]: Triggering myisam-recove                                                 r for all MyISAM tables
Sep 22 12:54:09 webserver ntpdate[664]: no server suitable for synchronization f                                                 ound

As for "options" under "fstab". Are there any reccomended settings i should use there? I've allready mounted 3 other partitions. "tmp" "var/www" and a random folder i made "Personlig" but i left the "options" blank.

---

### Post by WorMzy on 2011-09-22
Generally, I just use "default".

There's nothing in that log file that looks suspicious to me.

---

### Post by dcstar on 2011-09-22
> **johandsom3 said:**
> Hello fellow ubuntu users.

I'm pretty new to using ubuntu, and my boss told me to mount a partition in /usr.
.........

You do **not** stuff around with system folders. /usr is a system folder controlled by the system for system use and it does not tolerate users who do not know what they are doing mucking it up.

If you do not get the credentials of what you are copying - as well as the mounting - 100% right then you risk breaking your system.

---

### Post by johandsom3 on 2011-09-22
My system did not break...:p It has just gotten a tiny wound :) ( the start up )

Anyways, i do understand what you're talking about :)

This is a virtual server though, so if it does get broken, its not that dangerous : )

---

