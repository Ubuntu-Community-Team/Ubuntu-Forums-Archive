---
title: "Need help installing Moblock."
date: 2010-03-14
forum: General Help
---

### Post by Mountain Dew Overdose on 2010-03-14
Hello, I recently tried installing the IP block program for Linux, MoBlock, I need help with the aptitude method for installing it...every time I do the second command 'sudo aptitude install moblock blockcontrol', it says it can't find the package moblock...what am I doing wrong? I'm following the guide, really need help with this.

---

### Post by mikewhatever on 2010-03-14
What guide? I don't see any links to guides in your post.

---

### Post by Mountain Dew Overdose on 2010-03-14
This one [https://help.ubuntu.com/community/MoBlock](https://help.ubuntu.com/community/MoBlock) and this was the output of the command...

tyler@lintmagnet:~$ sudo aptitude install moblock blockcontrol
[sudo] password for tyler: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Couldn't find any package whose name or description matched "moblock"
Couldn't find any package whose name or description matched "blockcontrol"
Couldn't find any package whose name or description matched "moblock"
Couldn't find any package whose name or description matched "blockcontrol"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

tyler@lintmagnet:~$

---

### Post by mikewhatever on 2010-03-14
Have you added the repository as indicated? If you have, try running <sudo aptitude update> before installing.

---

### Post by Mountain Dew Overdose on 2010-03-14
Must have missed that...I did that, then aptitude update, then install, but now I get this and I dunno what to do...


tyler@lintmagnet:~$ sudo aptitude install moblock blockcontrol
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages are BROKEN:
  moblock 
The following NEW packages will be installed:
  blockcontrol 
0 packages upgraded, 2 newly installed, 0 to remove and 1 not upgraded.
Need to get 132kB of archives. After unpacking 545kB will be used.
The following packages have unmet dependencies:
  moblock: Depends: libnetfilter-queue1 (>= 0.0.15) which is a virtual package.
           Depends: libnfnetlink0 (>= 0.0.40) which is a virtual package.
Unable to resolve dependencies!  Giving up...
The following packages are BROKEN:
  moblock 
The following NEW packages will be installed:
  blockcontrol 
0 packages upgraded, 2 newly installed, 0 to remove and 1 not upgraded.
Need to get 132kB of archives. After unpacking 545kB will be used.
aptitude failed to find a solution to these dependencies.  You can solve them yourself by hand or type 'n' to quit.
The following packages have unmet dependencies:
  moblock: Depends: libnetfilter-queue1 (>= 0.0.15) which is a virtual package.
           Depends: libnfnetlink0 (>= 0.0.40) which is a virtual package.
Resolve these dependencies by hand? [N/+/-/_/:/?]

---

### Post by mikewhatever on 2010-03-14
Looks like a broken package.

**sudo apt-get install -f**

---

### Post by Mountain Dew Overdose on 2010-03-14
What exactly does that command do? 

tyler@lintmagnet:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
tyler@lintmagnet:~$ 

Nothing really happens that I notice...I'm new to Linux, sorry if I miss anything.

---

### Post by mikewhatever on 2010-03-14
It's supposed to fix broken packages. Run it, and then try installing.

---

### Post by Mountain Dew Overdose on 2010-03-14
Could you better explain how to use the command, in more detail? I tried running it and the package was still broken...

---

### Post by mikewhatever on 2010-03-14
You just run it, nothing special. You can also try the GUI version.
[https://help.ubuntu.com/community/SynapticHowto#How%20to%20fix%20broken%20packages](https://help.ubuntu.com/community/SynapticHowto#How%20to%20fix%20broken%20packages)

---

### Post by Mountain Dew Overdose on 2010-03-14
I tried fixing the broken packages like it says, nothing at all happens =/ I go into synaptic package, I did exactly as that page said to fix broken packages, and nothing happens...

---

### Post by mikewhatever on 2010-03-14
I don't think anything significant is supposed to happen, no fireworks or fanfares. I can only guess that by saying 'nothing happens', you mean that the broken package doesn't get fixed. Is that correct?

---

### Post by Mountain Dew Overdose on 2010-03-15
Yea, it didn't fix it...dammit, it shouldn't be this difficult!

---

### Post by jre on 2010-03-21
Have you added the correct lines to your /etc/apt/sources.list?
E.g. if you are running karmic, then you need to add the lines containing **karmic** there.

---

### Post by Mountain Dew Overdose on 2010-03-28
After giving up on MoBlock for a week, I decided to go back and try and install it again, I did everything and tried to get the packages from Synaptic Package Manager, I mark Moblock for installation and I get a window with this.

```
moblock:
 Depends: libnetfilter-queue1 (>=0.0.15) but it is not installable
 Depends: libnfnetlink0 (>=0.0.40) but it is not installable
 Recommends: blockcontrol but it is not going to be installed
```

---

### Post by jre on 2010-03-28
Please tell us your distribution (e.g. Ubuntu 9.10 karmic) and the lines that you set in /etc/apt/sources.list.

Further please issue this command
```
sudo aptitude update
``` so that your system learns about any changes in sources.list.

---

### Post by Mountain Dew Overdose on 2010-03-28
FINALLY, after much googling, I figured out that my Universe repository wasn't checked in Software Sources, I checked it, and decided to try sudo apt-get install moblock, which the guide does not even mention to try, and worked flawlessly, I now have MoBlock :) Why does the guide not mention this? And it's 9.10 Ubuntu Karmic Koala.

---

### Post by jre on 2010-03-29
On [http://moblock-deb.sourceforge.net/](http://moblock-deb.sourceforge.net/) this information has always been there. I didn't know that this was missing in the ubuntu help wiki, but I've now added it there. Thanks for hinting me to this (but you might have edited the guide yourself).

Have fun

---

### Post by jrg3 on 2010-05-30
I'm needing help with essentially the same thing here. I've a dependency problem I'm guessing has something to do with Universe, but I'm not sure. I'm trying to install Moblock, which I've successfully done on many other boxes and distros, but I'm running into a dependency issue and I can't spot the source of the problem.

```
Please be patient ...
 * Starting IP block daemon moblock                                      [fail] 
invoke-rc.d: initscript blockcontrol, action "start" failed.
dpkg: error processing blockcontrol (--configure):
 subprocess installed post-installation script returned error exit status 8
dpkg: dependency problems prevent configuration of mobloquer:
 mobloquer depends on blockcontrol; however:
  Package blockcontrol is not configured yet.
dpkg: error processing mobloquer (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 blockcontrol
 mobloquer
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

And my sources.list
```
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted multiverse universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted universe
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse

## Chromium Daily Builds | jrg3
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu lucid main
deb-src http://ppa.launchpad.net/chromium-daily/ppa/ubuntu lucid main
deb http://archive.canonical.com/ lucid partner

## Google software repository | jrg3
deb http://dl.google.com/linux/deb stable non-free main

## Moblock software repository | jrg3
deb http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu lucid main
deb-src http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu lucid main
```

---

### Post by jre on 2010-05-30
> **jrg3 said:**
> but I'm running into a dependency issue and I can't spot the source of the problem.

```
 subprocess installed post-installation script returned error exit status 8

```
No, you have another problem. (So it would be better to start a new thread for your problem.) Your sources.list is ok. What happens is error 8 when trying to install blockcontrol. This indicates an iptables command failed.
I need either the previous output that you got while installing, or we might find something in /var/log/blockcontrol.log.

---

### Post by jrg3 on 2010-05-30
I solved the problem. All it took was you telling me that it wasn't a dependency issue. I was entering a typo'd entry at the #WHITE_TCP_OUT="http https" text prompt. Thanks for responding so quickly (as you always do).

---

