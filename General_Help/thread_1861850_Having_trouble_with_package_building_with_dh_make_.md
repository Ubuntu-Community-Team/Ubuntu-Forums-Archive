---
title: "Having trouble with package building with dh_make since Oneiric installation"
date: 2011-10-16
forum: General Help
---

### Post by inameiname on 2011-10-16
I am having an odd problem ever since I did a fresh installation of Oneiric. Basically, I am having trouble using 'dh_make' to build due to it popping pieces of random lines inside what it makes. I have no clue as to why this is happening. FYI, this extra stuff isn't just added terminal readout but gets thrown in all that dh_makes inside a package folder, and screws up a successful make and build.

In Natty, I used this code with dh_make, and it worked flawlessly:

```

$ dh_make -n -s -e myemail@address.com 
Maintainer name  : Me
Email-Address    : myemail@address.com 
Date             : Sun, 16 Oct 2011 04:10:45 -0400
Package Name     : my-package
Version          : 1.0-1~me
License          : gpl3
Type of Package  : Single
Hit <enter> to confirm: 

```Now, in Oneiric, I am finding this now:

```

$ dh_make -n -s -e myemail@address.com 
Maintainer name  : root
daemon
bin
sys
sync
games
man
lp
mail
news
uucp
proxy
www-data
backup
Mailing List Manager
ircd
Gnats Bug-Reporting System (admin)
nobody


colord colour management daemon

Light Display Manager
Avahi autoip daemon
Avahi mDNS daemon
usbmux daemon
PulseAudio daemon
RealtimeKit
Speech Dispatcher
HPLIP system user

Me



Email-Address    : myemail@address.com 
Date             : Sun, 16 Oct 2011 04:10:45 -0400
Package Name     : my-package
Version          : 1.0-1~me
License          : gpl3
Type of Package  : Single
Hit <enter> to confirm: 

```
At first I thought it was just some extra random readout, but later I found that some of it is part of my '/etc/passwd' file. Strange:

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
colord:x:102:105:colord colour management daemon,,,:/var/lib/colord:/bin/false
messagebus:x:103:107::/var/run/dbus:/bin/false
lightdm:x:104:108:Light Display Manager:/var/lib/lightdm:/bin/false
avahi-autoipd:x:105:112:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
avahi:x:106:113:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
usbmux:x:107:46:usbmux daemon,,,:/home/usbmux:/bin/false
pulse:x:109:119:PulseAudio daemon,,,:/var/run/pulse:/bin/false
rtkit:x:110:122:RealtimeKit,,,:/proc:/bin/false
speech-dispatcher:x:111:29:Speech Dispatcher,,,:/var/run/speech-dispatcher:/bin/sh
hplip:x:112:7:HPLIP system user,,,:/var/run/hplip:/bin/false
saned:x:113:123::/home/saned:/bin/false
me:x:1000:1000:Me,,,:/home/me:/bin/bash
ntp:x:114:125::/home/ntp:/bin/false
clamav:x:115:126::/var/lib/clamav:/bin/false
debian-tor:x:116:127::/var/lib/tor:/bin/bash

```Anybody ever had this before, or knows how to fix? Or maybe even just what changed from a fresh install of Natty versus Oneiric that would change it?

---

### Post by marcin_ant on 2011-10-16
[https://bugs.launchpad.net/ubuntu/+source/dh-make/+bug/875705](https://bugs.launchpad.net/ubuntu/+source/dh-make/+bug/875705)

---

### Post by inameiname on 2011-10-16
> **marcin_ant said:**
> [https://bugs.launchpad.net/ubuntu/+source/dh-make/+bug/875705](https://bugs.launchpad.net/ubuntu/+source/dh-make/+bug/875705)


Thanks for posting a bug about this issue. Good to know I am not the only one finding this a bit odd. Definitely a critical bug that needs fixed soon.

---

### Post by inameiname on 2011-10-20
As per that bug posting, there is a potential workaround for this issue.


replace:
   dh_make -n -s -e [EMAIL="myemail@address.com"]myemail@address.com[/EMAIL]
with:
   DEBFULLNAME="Me" dh_make -n -s -e [EMAIL="myemail@address.com"]myemail@address.com[/EMAIL]

        
I haven't tested this yet to see if it does indeed work in Oneiric. Those who have, feel free to comment on if it is a valid workaround.

---

### Post by cjwatson on 2011-10-22
> **inameiname said:**
> I am having an odd problem ever since I did a fresh installation of Oneiric. Basically, I am having trouble using 'dh_make' to build due to it popping pieces of random lines inside what it makes. I have no clue as to why this is happening. FYI, this extra stuff isn't just added terminal readout but gets thrown in all that dh_makes inside a package folder, and screws up a successful make and build.

Thanks for reporting this.  I've posted an analysis on the bug, and uploaded fixes to precise and oneiric-proposed.  The former should be published in an hour or so; the latter needs manual review but hopefully shouldn't take too long.

The most direct workaround is to run ```
export LOGNAME="$USER"
``` before running dh_make.

---

### Post by inameiname on 2011-10-23
> **cjwatson said:**
> Thanks for reporting this.  I've posted an analysis on the bug, and uploaded fixes to precise and oneiric-proposed.  The former should be published in an hour or so; the latter needs manual review but hopefully shouldn't take too long.

The most direct workaround is to run ```
export LOGNAME="$USER"
``` before running dh_make.


That is excellent. I appreciate it! Reading the bug report I saw that it seems its a lightdm issue. That makes sense.

I saw that dh-make in precise has already been updated: dh-make - 0.59ubuntu1. Guess I will just wait for the oneiric version to come out. 

In the meantime, are you saying what is needed (as a workaround), is to do this:

```

replace:
dh_make -n -s -e [EMAIL="myemail@address.com"]myemail@address.com[/EMAIL]
with:
export LOGNAME="$USER" dh_make -n -s -e [EMAIL="myemail@address.com"]myemail@address.com[/EMAIL]

```

And this:     DEBFULLNAME="Me", is not necessary?

---

### Post by cjwatson on 2011-10-23
> **inameiname said:**
> In the meantime, are you saying what is needed (as a workaround), is to do this:

```

replace:
dh_make -n -s -e [EMAIL="myemail@address.com"]myemail@address.com[/EMAIL]
with:
export LOGNAME="$USER" dh_make -n -s -e [EMAIL="myemail@address.com"]myemail@address.com[/EMAIL]

```

And this:     DEBFULLNAME="Me", is not necessary?

If you're going to put it all in one command then drop the 'export':

```
LOGNAME="$USER" dh_make -n -s -e
```

Setting LOGNAME works around the problem a little further up the chain of events than setting DEBFULLNAME, so you don't need to set both, no.

---

### Post by inameiname on 2011-10-23
> **cjwatson said:**
> If you're going to put it all in one command then drop the 'export':

```
LOGNAME="$USER" dh_make -n -s -e
```Setting LOGNAME works around the problem a little further up the chain of events than setting DEBFULLNAME, so you don't need to set both, no.

Oh ok. Thank you! I will use that then until the update comes in Oneiric. Very nice. :)

---

### Post by MG&amp;TL on 2011-10-29
Just to say thanks. :D

---

### Post by inameiname on 2011-10-29
For those who don't know yet, this bug has been fixed in the latest oneiric-proposed repository. No need to add anything extra than what you are used to.

By the way, I have used the latest dh-make in Oneiric many times now to build packages and it has worked flawlessly.

Thank you all who helped fixed this bug.

---

### Post by MG&amp;TL on 2011-10-29
Okay. Still not working properly here, but I'm not getting proposed updates.

---

### Post by inameiname on 2011-10-29
> **MG&TL said:**
> Okay. Still not working properly here, but I'm not getting proposed updates.

Hmm, well then, I suggest adding the oneiric-proposed repo, if not for this one update only. You can always remove it later. 

Just open 'Software Sources' to enable it. Or you can try downloading it manually. Oddly the oneiric-proposed repo version isn't available here: [http://packages.ubuntu.com/search?keywords=dh-make&suite=default&section=all&arch=any&searchon=names](http://packages.ubuntu.com/search?keywords=dh-make&suite=default&section=all&arch=any&searchon=names), but I think the precise version is the same, and will work (not 100% on that, though).

---

### Post by MG&amp;TL on 2011-10-30
Meh. If it breaks, it breaks. :D

---

### Post by inameiname on 2011-10-30
> **MG&TL said:**
> Meh. If it breaks, it breaks. :D

Hehe. Well, I for one has never had issues with anything in oneiric-proposed repo, as they seem to test it well enough before even putting it in there, so I'm sure you will be fine using it.

---

