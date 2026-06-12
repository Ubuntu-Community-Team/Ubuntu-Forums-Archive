---
title: "User exists but not visible in list of users"
date: 2009-11-04
forum: General Help
---

### Post by Oliver Woodford on 2009-11-04
Hi all

I have a workstation running 64-bit Ubuntu 9.10 at work. The /home directory is mapped to a directory on a server on our network, where we all have our own user directories.

When I power up the workstation, at the graphical login prompt it allows me to login as Mark or Other... Since my username is Oliver, I click other and type in my username and password. However, I want my username to be in the list so I don't have to do that. I've looked at the admin tools, and I can't do this because I'm not in the list of users shown when I go to System->Administration->Users and Groups. If I try to add myself to that list it says the username already exists. So why don't I appear in that list?

My user id is something like 756. Mark's is like 1005. His is the only user id over 1000.

Thanks,
Oliver

---

### Post by soapBAR2 on 2009-11-04
Hello, please post the contents of /etc/passwd.

---

### Post by goldencako on 2009-11-04
Hey, I'm having exactly the same problem as Oliver. I have manually added a guest account, named **visita** that shows up on login and *Users and Groups*. My account, **cako** shows on neither.

Here's my \etc\passwd

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
syslog:x:101:102::/home/syslog:/bin/false
messagebus:x:102:106::/var/run/dbus:/bin/false
hplip:x:103:7:HPLIP system user,,,:/var/run/hplip:/bin/false
avahi-autoipd:x:104:110:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
avahi:x:105:111:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
couchdb:x:106:113:CouchDB Administrator,,,:/var/lib/couchdb:/bin/bash
haldaemon:x:107:114:Hardware abstraction layer,,,:/var/run/hald:/bin/false
speech-dispatcher:x:108:29:Speech Dispatcher,,,:/var/run/speech-dispatcher:/bin/sh
kernoops:x:109:65534:Kernel Oops Tracking Daemon,,,:/:/bin/false
saned:x:110:116::/home/saned:/bin/false
pulse:x:111:117:PulseAudio daemon,,,:/var/run/pulse:/bin/false
gdm:x:112:119:Gnome Display Manager:/var/lib/gdm:/bin/false
cako:x:999:999:Carlos,,,:/home/cako:/bin/bash
Slmodemd:x:113:121:Smart Link Modem Server,,,:/var/log/slmodemd:/bin/false
visita:x:1000:100:Visita,,,,:/home/visita:/bin/bash
```

---

### Post by goldencako on 2009-11-06
Fixed it. It really did have to do with the UID. I digged around and found out that for them to show on the login screen, UID has to be >999.
So, logout (I suggest reboot), and login as root. I preferred to just login from another tty. Then just excute
```
usermod -u NEW_UID USER
```
Needless to say, NEW_UID must be unique and over 999.

Hope it helps!

---

### Post by lensman3 on 2009-11-06
That is a bug.  User IDs less than 512 used to be system level userids.  Now Ubuntu has arbitrarily changed it to 1000 (why not 1012?). Ubuntu leave this alone!!!!!  The 512 has been around for 20 years.  This will probably screw up the rest of the Unix world (OS X, Sun, etc).

---

### Post by falconindy on 2009-11-06
> **lensman3 said:**
> That is a bug.  User IDs less than 512 used to be system level userids.  Now Ubuntu has arbitrarily changed it to 1000 (why not 1012?). Ubuntu leave this alone!!!!!  The 512 has been around for 20 years.  This will probably screw up the rest of the Unix world (OS X, Sun, etc).
Sorry but Ubuntu is **not** the first and only distro to be using 1000 as the starting point for non-system users. You probably also meant 1024, no?

Linux isn't Unix.

---

### Post by goldencako on 2009-11-06
[[COLOR="RoyalBlue"]This[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/99265") is an old bug which has been confirmed, but remains unsettled.

Now, it appears as though Ubuntu does in fact start from 1000 by default: [[COLOR="RoyalBlue"]source[/COLOR]]("http://www.linfo.org/uid.html")

Either way, 1000 is here to stay.

---

### Post by Oliver Woodford on 2009-11-09
Thanks for all the replies. Unfortunately my user id is set by the sys admin here at work so I can't change it. The limit of 1000 is therefore quite a pain.

---

### Post by goldencako on 2009-11-09
That *is* a pain. I think your best bet is to talk to him as ask for him to change it. All the other solutions that involve changing the system to allow 500+ users to be non-admin involve messing around with things you probably would't be allowed to change... Anyways, good luck with that!

---

