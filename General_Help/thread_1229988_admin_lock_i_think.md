---
title: "admin lock? i think"
date: 2009-08-02
forum: General Help
---

### Post by Numblp1234567 on 2009-08-02
I am EXTREMELY new to Ubuntu and really don't know anything. I changed the only user on this computer to a different name and when i tried to re log in it said the directory for the new name /home does not exist and I went into terminal and made a new user. When i try to upgrade anything it says something about contacting the local administrator (After i enter the passwords to upgrade or download things). Is there any way for me to get my original directory back or to fix this user to where I can upgrade my flash? Much help is appreciated!

I dont think i have Ubuntu 8.04 I might have lower, but I cannot upgrade... it says downloading file 2 of 2 and that the upgrade tool will help me and then it exits out and nothing pops up. also the message i get when i try to install adobe flash ( with GDebi) AFTER i enter the admin pass is: Failed to run gdebi-gtk '--non-interactive' '/tmp/install_flash_player_10_linux.deb' as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.

---

### Post by Numblp1234567 on 2009-08-02
also the original home directory user or w/e was called home/des and i changed my username to jibri and it changed the home/des to home/jibri and it says that home/jibri does not exist... in the terminal i type in /home/des and it says that exists still... any help????

so i think i have it down to this.... I changed "des" to jibri and now it is under the group des. I can't log onto the admin jibri at all because the directory home/jibri does not exist... but home/des does... how can i change home/jibri back to home/des?

---

### Post by michy99 on 2009-08-02
Enter these three commands in a terminal and post the results here:```
ls -l /home
cat /etc/passwd
cat /etc/group
```

---

### Post by Numblp1234567 on 2009-08-02
for the first command i got:

drwxr-xr-x 51 jibri des  4096 2009-08-01 19:20 des
drwxr-xr-x 22 lol   lol  4096 2009-08-02 20:12 lol
drwxr-xr-x 31 test  test 4096 2009-08-02 21:22 test

for the second command i got:

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

for the third command i got:

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

---

### Post by michy99 on 2009-08-02
Do you have a Live CD you can boot from?

---

### Post by Numblp1234567 on 2009-08-02
I'm pretty sure I don't... My mom had gotten our computer back with Ubuntu but she is still friends with the person that put it on here and I'm sure he has the CD ... but is that the only way I can fix this?

---

### Post by michy99 on 2009-08-02
I think we can do it from recovery mode. Reboot and select recovery mode at the boot menu. Then select 'Drop to root shell prompt.'Then enter```
mv /home/des /home/jibri
```Then enter:```
exit
```Select 'Resume normal boot' and see if you can log in with the jibri account.

---

### Post by Numblp1234567 on 2009-08-02
Thanks I'll try it in a few because I'm a little busy atm so i may respond slow or tomorrow. :P

---

