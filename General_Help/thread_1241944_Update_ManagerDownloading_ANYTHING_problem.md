---
title: "Update Manager/Downloading ANYTHING problem"
date: 2009-08-16
forum: General Help
---

### Post by Numblp1234567 on 2009-08-16
I get this when i try to download anything really. But it's more important for me to download flash then anything else at the moment. Can someone please help?
Message I get after trying to install package:

Failed to run gdebi-gtk '--non-interactive' '/tmp/install_flash_player_10_linux.deb' as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.

---

### Post by michy99 on 2009-08-16
It sounds like you are not a member of the admin group. What do you get when you enter this command in a terminal?```
groups
```

---

### Post by Numblp1234567 on 2009-08-16
test@unown:~$ groups
test

i know the admin group is des but i dont know how to change to the admin group...

---

### Post by michy99 on 2009-08-16
The first user set up when you install Ubuntu is a member of the admin group. Either you are using a different account which does not have admin privileges, or you have somehow messed up your groups.

---

### Post by Numblp1234567 on 2009-08-16
yeah i've messed them up for sure... I just don't know how to fix it and I don't have my recovery disk for Windows or Ubuntu :(

---

### Post by michy99 on 2009-08-16
What is the output of this command?```
cat /etc/group
```

---

### Post by Numblp1234567 on 2009-08-16
test@unown:~$ cat /etc/group
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:jibri
tty:x:5:
disk:x:6:
lp:x:7:cupsys
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:cupsys,jibri
fax:x:21:
voice:x:22:
cdrom:x:24:haldaemon,jibri
floppy:x:25:haldaemon,jibri
tape:x:26:
sudo:x:27:
audio:x:29:jibri
dip:x:30:jibri
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:jibri
sasl:x:45:
plugdev:x:46:haldaemon,jibri
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
dhcp:x:101:
syslog:x:102:
klog:x:103:
scanner:x:104:cupsys,hplip,jibri
nvram:x:105:
messagebus:x:106:
ssl-cert:x:107:cupsys
crontab:x:108:
ssh:x:109:
avahi-autoipd:x:110:
avahi:x:111:
netdev:x:112:jibri
lpadmin:x:113:jibri
haldaemon:x:114:
powerdev:x:115:haldaemon,jibri
slocate:x:116:
admin:x:117:jibri
gdm:x:118:
fuse:x:119:
des:x:1000:
vboxusers:x:120:jibri
test:x:1001:
lol:x:1002:
test@unown:~$

---

### Post by michy99 on 2009-08-16
Did you have a user named jibri that you changed to something else? Or a user that you changed to jibri? Post the output of ```
cat /etc/passwd
ls -l /home
```

---

### Post by Numblp1234567 on 2009-08-16
the original and only account was named des. I changed the username to jibri and it asked me if i wanted to change the directory /home/des to /home/jibri so I did it. I log out then moved the computer in my room and I now had to log on failsafe on jibri. So i made a new user named test just so i could use my internets and pidgin messenger. by the way i got this:

test@unown:~$ cat /etc/passwd
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/bin/sh
man:x:6:12:man:/var/cache/man:/bin/sh
lp:x:7:7:lp:/var/spool/lpd:/bin/sh
mail:x:8:8:mail:/var/mail:/bin/sh
news:x:9:9:news:/var/spool/news:/bin/sh
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:13:proxy:/bin:/bin/sh
www-data:x:33:33:www-data:/var/www:/bin/sh
backup:x:34:34:backup:/var/backups:/bin/sh
list:x:38:38:Mailing List Manager:/var/list:/bin/sh
irc:x:39:39:ircd:/var/run/ircd:/bin/sh
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
dhcp:x:100:101::/nonexistent:/bin/false
syslog:x:101:102::/home/syslog:/bin/false
klog:x:102:103::/home/klog:/bin/false
messagebus:x:103:106::/var/run/dbus:/bin/false
avahi-autoipd:x:104:110:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
avahi:x:105:111:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
cupsys:x:106:113::/home/cupsys:/bin/false
haldaemon:x:107:114:Hardware abstraction layer,,,:/home/haldaemon:/bin/false
hplip:x:108:7:HPLIP system user,,,:/var/run/hplip:/bin/false
gdm:x:109:118:Gnome Display Manager:/var/lib/gdm:/bin/false
jibri:x:1000:1000:Jibri,,,,:/home/Jibri:/bin/bash
test:x:1001:1001:Raven,5,555,5,5:/home/test:/bin/bash
lol:x:1002:1002:jibri,65,65,65,65:/home/lol:/bin/bash

test@unown:~$ ls -l /home
total 12
drwxr-xr-x 51 jibri des  4096 2009-08-01 19:20 jibri
drwxr-xr-x 23 lol   lol  4096 2009-08-05 00:13 lol
drwxr-xr-x 38 test  test 4096 2009-08-16 13:35 test

---

### Post by michy99 on 2009-08-16
Ok, it looks like the jibri account has admin privileges, so log in with that account. then backup the group file and open it as root:```
sudo cp /etc/group /etc/group.backup
gksudo gedit /etc/group
```Replace everything in the file with this:```
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:jibri,test,lol
tty:x:5:
disk:x:6:
lp:x:7:cupsys
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:cupsys,jibri,test,lol
fax:x:21:
voice:x:22:
cdrom:x:24:haldaemon,jibri,test,lol
floppy:x:25:haldaemon,jibri,test,lol
tape:x:26:
sudo:x:27:
audio:x:29:jibri,test,lol
dip:x:30:jibri,test,lol
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:jibri,test,lol
sasl:x:45:
plugdev:x:46:haldaemon,jibri,test,lol
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
dhcp:x:101:
syslog:x:102:
klog:x:103:
scanner:x:104:cupsys,hplip,jibri,test,lol
nvram:x:105:
messagebus:x:106:
ssl-cert:x:107:cupsys
crontab:x:108:
ssh:x:109:
avahi-autoipd:x:110:
avahi:x:111:
netdev:x:112:jibri,test,lol
lpadmin:x:113:jibri,test,lol
haldaemon:x:114:
powerdev:x:115:haldaemon,jibri,test,lol
slocate:x:116:
admin:x:117:jibri,test,lol
gdm:x:118:
fuse:x:119:
des:x:1000:
vboxusers:x:120:jibri,test,lol
test:x:1001:
lol:x:1002:
```Save the file. Reboot the computer and everything should work.

---

### Post by Numblp1234567 on 2009-08-16
is there a way to log in as jibri on this acc in terminal? or how do you paste because i dont know how to put the last code in being on a different account as failsafe

---

### Post by michy99 on 2009-08-16
Ctrl+Alt+F2 will get you a terminal. Log in as jibri and run this command:```
sudo adduser test admin
```Ctrl+Alt+F7 will get you back. Then reboot the computer and log in as test. test should now have admin privileges so you can make the changes in my last post.

---

### Post by Numblp1234567 on 2009-08-16
ok it got me admin privelages and I can download things but i get this message now after it tried downloading it AND i don't know what version of Ubuntu I have... and thanks so much so far for everything

message: 
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.159.0ubuntu1~gutsy1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.159.0ubuntu1~gutsy1_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]

---

### Post by michy99 on 2009-08-16
Go to System -> Administration -> Software Sources. Where it says 'Download from' choose a different server and try again.

---

### Post by slakkie on 2009-08-16
You are running Gutsy, which is EOL. I would advise you to upgrade, but given the mess that you've made I would strongly advise to clean install 8.04/8.10 or 9.04.

If you don't have a separate partition for /home, I would advise you to make a backup of your /home directory on a external disk and reinstall a supported version of Ubuntu, preferably 8.04 or 9.04. Also, if you didn't have /home as a seperate partition, please create one on your new installation!

---

