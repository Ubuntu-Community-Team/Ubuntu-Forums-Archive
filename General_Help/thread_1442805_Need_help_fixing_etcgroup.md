---
title: "Need help fixing /etc/group"
date: 2010-03-30
forum: General Help
---

### Post by Calash on 2010-03-30
Ubuntu 9.10 x64

The other day my computer lost it's /etc/group file, causing all sorts of issues.  Took a bit of time to narrow down the issue but I was able to get the system up and running.  However I am still having various problems such as -

usb not auto mounting
users-admin and time-admin returning "The Configuration could not be loaded" errors
no sound


I am thinking at this point that the root cause is still my group file.  I grabbed a default one from the web but still had to add an entry for gdm and one for virtualbox to get things somewhat started.  It would be a huge help if somebody could take a look at what I have now and let me know what it is missing.


```

root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:XXXXX
tty:x:5:
disk:x:6:
lp:x:7:cupsys
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:XXXXX,cupsys
fax:x:21:
voice:x:22:
cdrom:x:24:XXXXX
floppy:x:25:XXXXX
tape:x:26:
sudo:x:27:
audio:x:29:XXXXX
dip:x:30:XXXXX
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:XXXXX
sasl:x:45:
plugdev:x:46:XXXXX,haldaemon
staff:x:50:
games:x:60:
users:x:100:XXXXX
nogroup:x:65534:
dhcp:x:101:
syslog:x:102:
klog:x:103:
XXXXX:x:1000:XXXXX
lpadmin:x:104:XXXXX
scanner:x:105:XXXXX
admin:x:106:XXXXX
crontab:x:107:
ssh:x:108:
messagebus:x:109:
haldaemon:x:110:
slocate:x:111:
gdm:x:113:
vboxusers:x:1001:XXXXX

```


XXXXX is the username of the first user (only user at this point).


Edit: Apparently I also lost the ability to reboot or shutdown from gnome.  Sudo Halt still works.

---

### Post by Calash on 2010-03-31
I have gotten most of my issues worked out. The primary problems I was having with the USB, sound, and user admin area were due to the messagebus group not having the correct id after I recreated it.


To resolve I went into the /etc/passwd file and found the group ID that it was using as it was listed with the messagebus user (the second number).  Then I edited the group file to use that number and rebooted.

This link helped me narrow down the root cause of my problems.
[https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/295405](https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/295405)

I hope this helps out others who run into similar issues.

---

