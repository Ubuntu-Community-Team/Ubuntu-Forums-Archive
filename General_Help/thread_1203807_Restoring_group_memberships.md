---
title: "Restoring group memberships"
date: 2009-07-03
forum: General Help
---

### Post by youShotWhoInTheWhatNow on 2009-07-03
So I was dumb and did a 'usermod -G' command instead of 'usermod -g' and now I lost all my group memberships.  I booted into recovery mode and added myself back to the admin group so that I can at least perform sudo commands. Unfortunately, when I added myself to the admin group it overwrote /var/backups/group.bak with the useless version. So now I am not sure what all the groups are I should be part of.

From this page: [http://ccollins.wordpress.com/2007/07/02/restore-default-ubuntu-groups/](http://ccollins.wordpress.com/2007/07/02/restore-default-ubuntu-groups/) I was able to deduct that I need the following group memberships: bmoloney(my username), adm, uucp, dialout, cdrom, floppy, audio, dip, video, plugdev, scanner, netdev, lpadmin, powerdev, admin

However I am sure there is more groups I need membership in since I have installed quite a bit of software.  Here is my /etc/group file:

```
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:
tty:x:5:
disk:x:6:
lp:x:7:cupsys
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:cupsys
fax:x:21:
voice:x:22:
cdrom:x:24:haldaemon
floppy:x:25:haldaemon
tape:x:26:
sudo:x:27:
audio:x:29:pulse
dip:x:30:
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:
sasl:x:45:
plugdev:x:46:haldaemon
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
dhcp:x:101:
syslog:x:102:
klog:x:103:
scanner:x:104:cupsys,hplip
nvram:x:105:
messagebus:x:106:
ssl-cert:x:107:cupsys,postgres
crontab:x:108:
ssh:x:109:
avahi-autoipd:x:110:
avahi:x:111:
netdev:x:112:
lpadmin:x:113:
haldaemon:x:114:
powerdev:x:115:haldaemon
admin:x:117:
gdm:x:118:
fuse:x:119:
bmoloney:x:1000:
libuuid:x:120:
pulse:x:121:root
pulse-access:x:122:root
pulse-rt:x:123:root
sambashare:x:124:
mlocate:x:125:
polkituser:x:126:
winbindd_priv:x:127:
Debian-exim:x:116:
mysql:x:128:
postgres:x:129:
TemplateAdmins:x:1001:bmoloney
```

Can anyone point out other groups (besides those listed above) that I should be a member of?  By the way, I am running 8.10.

---

### Post by geirha on 2009-07-03
The easiest way to find out is to create a new Administrative user with System -> Administration -> Users and groups, and add your user to the same groups as that new user.

And when you install applications that add new groups, you don't get automatically added to that group, and you usually shouldn't add yourself manually either.

---

