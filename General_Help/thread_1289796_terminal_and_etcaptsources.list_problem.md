---
title: "terminal and /etc/apt/sources.list problem"
date: 2009-10-12
forum: General Help
---

### Post by brubblu on 2009-10-12
Hello,
I am a newbie regarding to linux, so I probably did something I shouldn't and I am unable to resolve my problem. Hope someone can help me...

So, it all started when I tried installing Firefox 3.5 (eventually failing for some unknown reason to me).
I followed a guide at [ this ]("http://www.stilegames.com/2009/07/02/come-installare-firefox-3-5-su-linux-ubuntu.html") thread, it is in italian, but the codes are the same in any language, i think.

I started to get this output for some commands i entered in the terminal (like sudo apt-get update or sudo apt-get install *anything*):

E: Il tipo '&#8216;deb' non è riconosciuto alla linea 54 nella lista sorgenti /etc/apt/sources.list

I am sorry, i have Ubuntu installed in Italian only on my system, and I think I wouldn't be able to translate this message properly...
Any help would be appreciated!
Brubblu

edit: now that I see it, it seems that the last user who left a comment, had my same problem...

---

### Post by falconindy on 2009-10-12
Looks like there's an error in line 54 of your sources.list file.

---

### Post by brubblu on 2009-10-12
yes, that was my understanding, but the questions are: which error it is? why did it happen? and most important, how to solve it?

---

### Post by Giblet5 on 2009-10-12
From a terminal window, type ```
sudo gedit +42 /etc/apt/sources.list
```

What is text of that line?

---

### Post by falconindy on 2009-10-12
> **brubblu said:**
> yes, that was my understanding, but the questions are: which error it is? why did it happen? and most important, how to solve it?
Post the contents of your /etc/apt/sources.list and we'll take a look.

---

### Post by brubblu on 2009-10-13
this is the content of resources.list:

```
#deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://it.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://it.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://it.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://it.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://it.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://it.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://it.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://it.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://it.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://it.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://it.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://it.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://it.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://it.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse
'deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu jaunty main'
'deb-src http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu jaunty main'
```

---

### Post by zer0x on 2009-10-13
Hi,

Its the punctuation marks wrapped around the last 2 lines, just remove those and it should work :D

HTH

zer0x

---

### Post by brubblu on 2009-10-13
Hehe thank you for your help, I almost can't believe it was so simple :)

---

