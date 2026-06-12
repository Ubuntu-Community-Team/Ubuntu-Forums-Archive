---
title: "deleted all groups"
date: 2009-09-20
forum: General Help
---

### Post by broken_symmetry on 2009-09-20
Hi guys,

I very foolishly appear to have completely ruined my groups. Using the 'users and groups' gui (unlocking root along the way) I believe I deleted EVERY group. Now, even if I create a new user, the result of the command 'groups' is just: username

In addition, upon boot, I get all sorts of errors, as even the root account does not belong to any groups.

I am running 64 bit 9.04, so ideally I need someone to tell me the default groups that I need to recreate (probably using 'id on the command line)

Is there any easy way to restore the default groups? Also, is it important for some of the default groups to have the same gid as they did before?

This horrible mistake was all caused by me trying to add the groups 'pulseaudio', 'pulseaudio-rt' etc.

Thanks,

-NM

---

### Post by tgeer43 on 2009-09-20
If I can find a command that will output the names and id#'s of *all* groups I can give you the list. The 'id' command only returns group info for a specified user. My understanding is that the group id #'s *are* significant. You're still going to have the problem of which users are members of which groups. If you're not the only user on the system then this could be extremely difficult.

tgeer

---

### Post by broken_symmetry on 2009-09-21
Hey tgeer,

I think the output of 'cat /etc/group' might work.

Thanks in advance for the help,

-NM

---

### Post by tgeer43 on 2009-09-21
My 9.04 AMD64 is far from a fresh install so no guarantee that the groups list is virgin. Also note that the groups that I belong to represent all of the administrative privileges that a regular user can have and is *not* the default setup. Anyway, here it is:
```
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:tgeer
tty:x:5:
disk:x:1001:tgeer
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:tgeer
fax:x:21:tgeer
voice:x:22:
cdrom:x:24:tgeer
floppy:x:25:
tape:x:26:tgeer
sudo:x:27:
audio:x:29:pulse,tgeer
dip:x:30:tgeer
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:tgeer
sasl:x:45:
plugdev:x:46:tgeer
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
libuuid:x:101:
syslog:x:102:
klog:x:103:
fuse:x:104:tgeer
ssl-cert:x:105:
lpadmin:x:106:tgeer
crontab:x:107:
mlocate:x:108:
ssh:x:109:
avahi-autoipd:x:110:
gdm:x:111:
netdev:x:112:tgeer
saned:x:113:
pulse:x:114:
pulse-access:x:115:
pulse-rt:x:116:
messagebus:x:117:
polkituser:x:118:
avahi:x:119:
haldaemon:x:120:
admin:x:121:tgeer
tgeer:x:1000:
sambashare:x:122:tgeer
postfix:x:123:
postdrop:x:124:
winbindd_priv:x:125:
ntp:x:126:
```Good luck,

tgeer

---

### Post by broken_symmetry on 2009-09-21
Much better! Thanks a ton.

-NM

---

### Post by sisco311 on 2009-09-21
why don't you use the backup of the file: /etc/group-
just make sure that the permissions are set correctly: 0644

---

### Post by IndigoSpike on 2011-02-28
> **sisco311 said:**
> why don't you use the backup of the file: /etc/group-
just make sure that the permissions are set correctly: 0644


I get "bash: /etc/group-: Permission denied"


Edit: Wait a second. I feel so dang n00b... Sorry guys, I think I am missing something here. How do I find the backup?

I, not knowing what I'm doing ( D'OH! ), deleted all my groups as well. I had to reset my root password... That wasn't too hard. Now, I went through the groups and I think most were back again. So I added my user to every single group except "nogroup". I need to stop before I dig too big of a hole, right? LOL. So, when I install an app ( right now it's Audacity ) I get errors like this one:

> installArchives() failed: dpkg: unrecoverable fatal error, aborting: 
 syntax error: unknown group 'crontab' in statoverride file


Nevermind. I just re-installed Ubuntu. Thanks, though. =]

---

