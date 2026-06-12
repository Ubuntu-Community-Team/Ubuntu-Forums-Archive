---
title: "How do i update ubuntu software center ?"
date: 2012-10-13
forum: General Help
---

### Post by CCgirl6690 on 2012-10-13
Hello 
i noticed on ubuntu 12's software center there are some newest apps than ubuntu 10's software center , 
exammple: java 7 in ubuntu 12  and java 6 on ubuntu 10  
same thing about pidgin i was trying to get the plugins pack for my pidgin and it insalled an older version of on ubuntu 10  while its got the new version on the latest  ubuntu 12 
so my question is 
are there anyway to update the ubuntu software itself???
thank you...............
love this forum .........................

---

### Post by critin on 2012-10-13
I'm sure there are ways but I'd wait for expert advice.
In the meantime, just a note of caution to inform yourself.  Read starting at:
PPA's:  Silver Sword or Golden Band-Aid

[http://www.thepowerbase.com/2012/04/how-to-fix-broken-packages-in-ubuntu-or-debian/](http://www.thepowerbase.com/2012/04/how-to-fix-broken-packages-in-ubuntu-or-debian/)

---

### Post by kbrodenhau on 2012-10-14
Probably in your Software Center, there is a Edit -> Software Sources...

So from my Ubuntu 12.04 (Precise) Software Center, I have the following repositories (as listed in my /etc/apt/sources.list file). 

But BE WARNED that this may cause problems to your older distro by using newer packages!!! 

You ought read this first as well -- [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)


Anyway, here is my list of 12.04 Precise repositories...

# deb cdrom:[Lubuntu 12.04 _Precise Pangolin_ - Release i386 (20120423)]/ precise main multiverse restricted universe

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu) precise main
deb-src [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu) precise main
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) precise free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) precise free non-free
# deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) precise contrib
# deb-src [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) precise contrib
deb [http://packages.mate-desktop.org/repo/ubuntu](http://packages.mate-desktop.org/repo/ubuntu) precise main
deb-src [http://packages.mate-desktop.org/repo/ubuntu](http://packages.mate-desktop.org/repo/ubuntu) precise main
deb [http://repo.mate-desktop.org/ubuntu](http://repo.mate-desktop.org/ubuntu) precise main
deb-src [http://repo.mate-desktop.org/ubuntu](http://repo.mate-desktop.org/ubuntu) precise main
# deb [http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu](http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu) precise main
# deb-src [http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu](http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu) precise main

---

### Post by zombifier25 on 2012-10-14
> **kbrodenhau said:**
> 
But BE WARNED that this may cause problems to your older distro by using newer packages!!!
> **kbrodenhau said:**
> [...]this may **cause problems** to your older distro[...]
> **kbrodenhau said:**
> [...][size=4]cause problems[/size][...]

If you want newer softwares in 12.04 to be in 10.04, there's no safer way than upgrading to 12.04. Or you can search for PPAs of specific programs, but there's no guarantee that they are safe as well.

---

### Post by CCgirl6690 on 2012-10-14
@ **kbrodenhau **thanks for the big reply  [B]kbrodenhau ,i will read it later , seems complete and to complicated for me to understand at the moment but thank you 

@zombiefier25   hi , could you please tell me what do you mean by not being safe using ppa?  
and for example i want to use latest Pidgin plugins pack , but how do i use ppa on it?  i could use the ppa for its main messenger so its the newest version ,
but not sure how to use it to update the plugins 
thank you   . 




[/B]

---

### Post by claracc on 2012-10-14
You cannot use a ppa belonging to a release as precise to update your software which belongs to other release, i.e. meerkat.

If you want to upgrade one program you'll have to upgrade your system ( I think ubuntu 10.10 is not longer supported, if it is what you have) or download the deb package and installing or looking for a ppa for your ubuntu version which mantains the program you want to update.

The safer way, as it has been said, is to use a ppa for your ubuntu version, if there is one.

---

### Post by CCgirl6690 on 2012-10-14
no one has yet to say what does it mean by SAFE . like refrain from bugs or viruses and such ?
thanks

---

### Post by Cheesemill on 2012-10-14
Basically the software versions are fixed for a specific version of Ubuntu when it is released, the only updates that you get are ones that fix bugs or security issues.

For example when Ubuntu 12.04 was released the latest version of Gimp was 2.6. Because of the way the updates work the only updates you get for Gimp using 12.04 will be 2.6.1, 2.6.2 etc.

Even though Gimp 2.8 has since been released it will never be available through the normal update process as it is a new version of the software, not just a bug fix or security fix.

The main way to get around this and have access to a newer version of the software is to use a PPA (personal package archive). PPA's are a way of adding later versions of software to the Software Centre on an older version of Ubuntu, however, because they are usually created by a single user they don't go through the usual testing procedures that they would do if they were released by Canonical using the standard upgrade procedure.

This is where 'unsafe' comes into it. By using a PPA you are installing software that hasn't been properly tested with Ubuntu so there could be stability and security issues that haven't yet been discovered. Also you are completely trusting that the user who has created the PPA has done so correctly.

I would basically boil it down to this:
If you are happy with the versions of software available on your system except for one or two applications then it is probably worth searching for PPA's that will let you install the newer versions on your system.
However, if you find that you want to install a lot up updated software then your best bet is to upgrade to the latest release of Ubuntu.

---

### Post by critin on 2012-10-14
> **CCgirl6690 said:**
> no one has yet to say what does it mean by SAFE . like refrain from bugs or viruses and such ?
thanks

The links posted and suggested for you to read to inform yourself,  explained the danger involved for those not experienced.   **Doing this could break your system.  (unsafe)**

A quote from the link in post 2:

*Adding a PPA channel to your system is stupidly simple, but once you’ve  done it and you’re not properly versed in Debian package management, you  may have destroyed your system.*

Installing 12.04 is the safest way to get the newer software created especially for that version.  Ubuntu changes at each release, nothing (or very little) remains the same.

---

