---
title: "sudo: unknown user: root"
date: 2010-10-30
forum: General Help
---

### Post by cyprys on 2010-10-30
Someone please tell me what should be in first line of */etc/passwd*, because I messed it up and now when I try to sudo anything I see:
**sudo: unknown user: root**

There is no root in /etc/passwd - I accidentally overwrote it with the following:
> 1 hdfdsasdf

I'm scared to death! Should I reboot? Or will my system stuck if I do? More descriptive story below.

> **$ sudo cat /etc/passwd | grep cypr**
*Oh, someone put a wrong name here. Not to worry, I'll fix this!*

**$ sudo vi /etc/passwd | grep cypr**
**ddihdfdsasdf**
*Fail! Nothing appears on the screen. I have to kill the terminal.*

**$ sudo vi /etc/passwd**
*A passwd.swp message? Let's fix this too!*
**(R)ecover**

**$ sudo vi /etc/passwd**
*What do you mean: "unknown user: root"?*

**$ vi /etc/passwd**
*Why the heck is this "readonly"!?*

---

### Post by cyprys on 2010-10-30
Managed it already... I'll download Ubuntu ISO, make a LiveUSB and boot it up, then put the following into the first line of */etc/passwd*:

**root:x:0:0:root:/root:/bin/bash**

Thank you **doc** from #ubuntu IRC channel on freenode!

---

### Post by efflandt on 2010-10-30
You should NEVER tamper with /etc/passwd or the pam stuff directly.  You should always use proper tools (commands).  You could fix it from an live/install CD (or bootable iso or system on USB).

My /etc/passwd looks like this.  Note that passwords are not actually stored in /etc/passwd, that is substituted with an "**x**" and passwords are actually stored somewhere else.  Your username would be in place of where my name **efflandt** is and their might be additional entries after that for some installed programs that need their own user or root access (just **sshd** on mine).

```
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
libuuid:x:100:101::/var/lib/libuuid:/bin/sh
syslog:x:101:103::/home/syslog:/bin/false
messagebus:x:102:105::/var/run/dbus:/bin/false
avahi-autoipd:x:103:108:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
avahi:x:104:109:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
couchdb:x:105:113:CouchDB Administrator,,,:/var/lib/couchdb:/bin/bash
usbmux:x:106:46:usbmux daemon,,,:/home/usbmux:/bin/false
speech-dispatcher:x:107:29:Speech Dispatcher,,,:/var/run/speech-dispatcher:/bin/sh
kernoops:x:108:65534:Kernel Oops Tracking Daemon,,,:/:/bin/false
pulse:x:109:114:PulseAudio daemon,,,:/var/run/pulse:/bin/false
rtkit:x:110:117:RealtimeKit,,,:/proc:/bin/false
saned:x:111:118::/home/saned:/bin/false
hplip:x:112:7:HPLIP system user,,,:/var/run/hplip:/bin/false
gdm:x:113:120:Gnome Display Manager:/var/lib/gdm:/bin/false
efflandt:x:1000:1000:David Efflandt,,,:/home/efflandt:/bin/bash
sshd:x:114:65534::/var/run/sshd:/usr/sbin/nologin
```Once you get that sorted out, if you are not using the gui to add users, see **man adduser** and **apropos user | less** for list of other man pages related to users.

---

### Post by cyprys on 2010-10-30
Thank you very much, I'll do this as soon as the ubuntu-netbook ISO downloads (this is a good excuse it to try it out and see the difference between desktop edition). Also, thank you for pointing out **apropos**. I didn't know such thing exists.

---

