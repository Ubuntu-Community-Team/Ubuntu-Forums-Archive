---
title: "Synaptic is not displaying packages from recently added repos"
date: 2009-07-12
forum: General Help
---

### Post by Kalanac on 2009-07-12
Hi, I'm currently installing Ubuntu on a laptop system for a friend who has seen us using it, likes it and is fed up with windows.

Everything is working fine except for one really weird glitch.  A lot of the packages are missing from synaptic.  The first one I noticed was missing was ubuntu-restricted-extras, I didn't think much of it at the time, I just double checked how to install that particular package and used apt-get command line installer which worked fine.

Then I was trying to show her how to install programs using synaptic which I thought should be there but they weren't.  I've copied my sources.list file from my own machine which works fine on both my desktop and laptop so I can't see the issue.

I've reloaded the package list a number of times both in synaptic and command line and I have deleted the .synaptic config file from root to start with a blank slate.  I double checked permissions of the /etc/apt folder and files therein, no problems (I did notice that the sources.list file had inherited the permissions of my friends account so I chowned and chgrped them back to root).

I've rebooted, the laptop a few times to no avail.

Now I know that synaptic can see the repositories because they appear in the "Show for files" list when reloading and the number of repositories polled matches those of my own machines.  I can also install packages just fine using command line.

If it was my own machine I would probably just put up with it and use command line, but as this system is for a brand new, recently converted linux user I don't want to put her off.

Are there any suggestions out there as to what the hell is going on here?

The laptop is an emachines D620, exactly the same model as my own laptop (which doesn't have this issue).  I'm using Ubuntu 9.04 Jaunty Jackalope, fresh install.

Hopefully

Kalanac

---

### Post by wojox on 2009-07-12
Both machine's are running Jaunty?

---

### Post by Kalanac on 2009-07-12
Yes, all machines are running exactly the same copy.

It's just occured to me that folk might want to see my sources.list so here it be:

```
# 
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
deb http://wine.budgetdedicated.com/apt jaunty main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope"
deb http://archive.ubuntu.com/ubuntu/ jaunty main universe restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty universe main multiverse restricted #Added by software-properties
```

I know that the CD-ROM duplicates but that doesn't seem to cause any issue on the other machines.

---

### Post by Kalanac on 2009-07-18
*bump*

Any ideas on this one guys?  If anyone needs further info I'll see what I can find.

---

### Post by drbee on 2009-07-18
Hi,  
I have the exact same problem! When I add a new repo it's not showing new packages in synaptic. If I do apt-get everything works fine. Jaunty 9.04 64bit

Please help..

---

### Post by Tman5293 on 2009-07-18
64 bit doesn't have all the packages that 32 bit because many packages don't support 64 bit operating systems

---

### Post by drbee on 2009-07-18
but it works with apt-get. And downloads amd64 packages.

---

### Post by cariboo on 2009-07-18
Your /etc/apt/sources.list seems to be missing a number of entries, compare it with the one in this [thread]("http://ubuntuforums.org/archive/index.php/t-997890.html").

---

### Post by drbee on 2009-07-18
Sorry but I think Kalanac problem is the same as mine and it's not about repo's. They work fine with apt-get so they update and work fine. The problem is synaptic that doesn't show the packages. For example I added the virtualbox repo through synaptic. Reloaded, but when i go to search for virtualbox 3 it's not there. If I do an apt-get install It works perfect, it finds the package and install it. Thanks for the help

---

### Post by mc4man on 2009-07-18
try running
```
sudo update-apt-xapian-index
```

(( which search are you using, the 'quick' or normal?

---

### Post by drbee on 2009-07-19
Thanks!!! That did it. Search now works for everything for me.. I was using the quick search by the way. Thank you again!!

---

### Post by drbee on 2009-07-20
Having to do that everytime I add a repo it's a little annoying... isn't there a way to fix it now that we know where the problem is?

---

### Post by DonL on 2009-09-02
I have the same machine and tried to upgrade to 9.04. Wish I could remember all the problems I had (lots) so I eventually re-installed 8.10 64bit. I know I'll have to upgrade eventually, and hopefully I'll have more patience then.
Can't say I had a problem with Synaptic though.

---

### Post by pazuzuthewise on 2010-04-14
I have now the same problem as [Kalanac]("http://ubuntuforums.org/member.php?u=866445") on a fresh install of xubuntu 9.10 i386.
It seems to refer to packages from the restricted category.
I couldn't find xubuntu-restricted-extras, nor sun-java-bin (the restricted repo was enabled in Software Sources).
But they appeared just fine in Ubuntu Software Center.
Not so for libdvdcss2, although I had added to the software sources the medibuntu repository and it's gpg key, and it installed with apt-get.
The os install was fresh, I didn't do any update prior to this happening.

---

