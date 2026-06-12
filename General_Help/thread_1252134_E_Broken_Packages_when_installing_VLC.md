---
title: "E: Broken Packages when installing VLC"
date: 2009-08-28
forum: General Help
---

### Post by RyCray on 2009-08-28
Hi, I'm fairly new to Linux, after installing UNR on my netbook I decided to install Ubuntu on my pc. 

I've been ok thus far, but I can't seem to find a solution for this error when i try to install VLC

> 
ryan@ryan-desktop:~$ sudo apt-get install vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  vlc: Depends: vlc-nox (= 0.9.9a-2ubuntu1) but it is not going to be installed
       Depends: libqtgui4 (>= 4.5.0~+rc1) but it is not going to be installed
       Depends: libsdl-image1.2 (>= 1.2.5) but it is not installable
E: Broken packages
I've tried fix broken packages in synaptic and it says Successfully fixed dependancy problems. But it didn't do anything. 

From reading other posts my sources.list file might be the problem but I couldn't find anything wrong with it.

> 
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty-proposed restricted main multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
Does anyone have any ideas?

---

### Post by mc4man on 2009-08-28
Your sources list looks ok though it's probably not a great idea to have proposed and to a lesser extent backports enabled by default. ( better to enable once and a while and ck. if there is an updated package(s) of use rather  than have proposed/ backpoted packages updated thru the update manager without picking specifically

So maybe to start go System -> Admin.. -> Software Sources and under the update tab leave the top 2 enabled and uncheck proposed and backports
Then click close and reload. ((if you choose not to do this then run this before procedding

sudo apt-get update

At that point try vlc again or try one of the mentioned packages singly, if a no go the error may be more specific

Ex.
```
sudo apt-get install libqtgui4
```

(the version # of the libqtgui4 to be installed must match the ver. # of the installed libqtcore4 exactly

---

### Post by credobyte on 2009-08-28
Have you tried to *force* package installation ?
```
sudo apt-get install -f vlc

```

---

### Post by michy99 on 2009-08-28
If you want the latest version of VLC, add this ppa to your sources:

[https://launchpad.net/~kow/+archive/ppa](https://launchpad.net/~kow/+archive/ppa)

Instructions for adding a PPA:

[https://launchpad.net/+help/soyuz/ppa-sources-list.html](https://launchpad.net/+help/soyuz/ppa-sources-list.html)

---

### Post by rajeev1204 on 2009-08-28
mc4man is correct,please try disabling backports,then do a...

```
sudo dpkg --configure -a 
```

Then run ```
sudo apt-get clean
``` and after that do a ..

```
sudo apt-get update
```

Probably a conflict with a newer vlc package.

Please report back here after trying.

---

### Post by RyCray on 2009-08-28
```
sudo apt-get install -f vlc
```Didn't work, gave the same error message.

I unchecked proposed and backports, reloaded and tried vlc again with no luck. So I tried apt-get on one of the unmet dependencies and got this:

```

ryan@ryan-desktop:~$ sudo apt-get install libqtgui4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  libqtgui4: Depends: libaudio2 but it is not installable
E: Broken packages
ryan@ryan-desktop:~$ sudo apt-get install libaudio2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libaudio2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libaudio2 has no installation candidate
ryan@ryan-desktop:~$ 

```**Discovered that this isn't only affecting vlc, I can't add anything from Add/Remove without getting this error:

> 
This application conflicts with other installed software. To install 'wesnoth-core' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.


**EDIT** 
> 
sudo apt-get clean

didn't do anything.

---

### Post by rajeev1204 on 2009-08-28
Please check my above post.

---

### Post by RyCray on 2009-08-28
@rajeev Followed your directions, same result :/

Would my 9600 gt driver have something to do with this?

I followed this [guide]("http://techstop.com.au/2008/05/hardy-nvidia-beta-drivers/") to get the driver installed. I got the newest driver from Nvidia and installed, while the installation was running something about the kernel came up, I didn't know what it ment so I gambled and clicked yes. 

Not sure if it's related at all but you never know, it's the first thing I did after I installed jaunty.

---

### Post by rajeev1204 on 2009-08-28
> **RyCray said:**
> @rajeev Followed your directions, same result :/

Would my 9600 gt driver have something to do with this?

I followed this [guide]("http://techstop.com.au/2008/05/hardy-nvidia-beta-drivers/") to get the driver installed. I got the newest driver from Nvidia and installed, while the installation was running something about the kernel came up, I didn't know what it ment so I gambled and clicked yes. 

Not sure if it's related at all but you never know, it's the first thing I did after I installed jaunty.

Probably not.Try step by step again

sudo dpkg --configure -a

sudo apt-get update

sudo apt-get upgrade.

---

### Post by RyCray on 2009-08-28
> 
ryan@ryan-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


Gives the same message each time.

---

### Post by RyCray on 2009-08-28
Problem solved. I don't know why but switching from "Server for Canada" to "Main Server" in the Ubuntu Software tab of the update window seems to have solved all my problems.

Thanks for the help guys.

---

### Post by mc4man on 2009-08-28
irrelevant

---

