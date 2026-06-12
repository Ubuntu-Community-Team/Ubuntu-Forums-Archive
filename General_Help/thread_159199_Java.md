---
title: "Java"
date: 2006-04-12
forum: General Help
---

### Post by shiznatix on 2006-04-12
I have been trying to install the latest version of java but without success. I get to this point

```

root@natix:/home/natix# fakeroot make-jpkg jre-1_5_0_04-linux-i586.bin
/usr/bin/fakeroot: line 150: make-jpkg: command not found

```

and so now I am stuck. Help please.

---

### Post by Perfect Storm on 2006-04-12
You might want to install a newer version.
Check here: [http://ubuntuforums.org/showthread.php?t=76735&highlight=java](http://ubuntuforums.org/showthread.php?t=76735&highlight=java)

---

### Post by shiznatix on 2006-04-12
root@natix:/home/natix# apt-get install fakeroot java-package java-common
Reading package lists... Done
Building dependency tree... Done
fakeroot is already the newest version.
E: Couldn't find package java-package

that is what i get when i try the other version...

---

### Post by Perfect Storm on 2006-04-12
you need to enable universe and multiverse first in your sourcelist.

---

### Post by WelterPelter on 2006-04-12
Do "sudo apt-get install java-package" and then try it again. It should work fine.

Ah -- too late.

---

### Post by shiznatix on 2006-04-12
...i have. everything is enabled. i did this on my laptop no problem but on my desktop im having troubles.

also somtimes when i am installing something with apt-get it somtimes just freezes mid way and i have to restart my computer to be able to use apt-get again.

---

### Post by Perfect Storm on 2006-04-12
Then I guess you have also run sudo apt-get update afterwards then.
Which structure and version do you run of Ubuntu?

How does your sourcelist looks like?

---

### Post by shiznatix on 2006-04-12
apt-get update did no good for me.

```

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb http://us.archive.ubuntu.com/ubuntu breezy universe
 deb-src http://us.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
 deb-src http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

 deb http://security.ubuntu.com/ubuntu breezy-security universe
 deb-src http://security.ubuntu.com/ubuntu breezy-security universe

```

thats my /etc/apt/sources.list

---

### Post by Perfect Storm on 2006-04-12
You need multiverse.

Add:

[b]## Multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse[/b]

```

sudo apt-get update

```

Then try the howto again.

---

### Post by shiznatix on 2006-04-12
awesome thank you. why did those not show up in my synaptic repository stuff? also while installing this I get to here

(Reading database ... 72420 files and directories currently installed.)
Unpacking java-package (from .../java-package_0.26_all.deb) ...

and it freezes. this is not the only time this has happened, it seams to happen every time i try to unpack a .deb file like this. I have to restart my computer to get anything to work agian through apt-get...why?

---

### Post by Perfect Storm on 2006-04-12
> awesome thank you. why did those not show up in my synaptic repository stuff? also while installing this I get to here

Partly because there's a risk when getting package from there (though I've never experienced it yet).

> and it freezes. this is not the only time this has happened, it seams to happen every time i try to unpack a .deb file like this. I have to restart my computer to get anything to work agian through apt-get...why?

I dunno why it's freezing I guess there's conflict/bug perhaps regarding some of your hardware. That's only a guess. You might start a new thread about it.

Does it happen when doing something like: sudo dpkg -i XXXXXX.deb?
You could try reinstall dpkg and see if it's make any diffrence.

---

