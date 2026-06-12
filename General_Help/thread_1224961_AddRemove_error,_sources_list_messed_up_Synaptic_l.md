---
title: "Add/Remove error, sources list messed up? Synaptic loads but can't install anything"
date: 2009-07-28
forum: General Help
---

### Post by Nisstyre56 on 2009-07-28
Okay, so I get this when I try and load add/remove.

Currently running **9.04**

```
This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.
```I ran sudo apt-get update, that seemed to work fine.

When I run sudo apt-get install -f I get the following error

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  postfix
Suggested packages:
  procmail postfix-mysql postfix-pgsql postfix-ldap postfix-pcre sasl2-bin
  resolvconf postfix-cdb
The following NEW packages will be installed:
  postfix
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
wesley@wes:~$ 

```I am not running synaptic or add/remove in the background when I do this...there is no other process of it running, I have rebooted and the same problem persists.

Please tell me if there is anything wrong with this sources list

```
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ca.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://ca.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ca.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://ca.archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb http://ca.archive.ubuntu.com/ubuntu/ jaunty-security universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ jaunty-security universe
deb http://ca.archive.ubuntu.com/ubuntu/ jaunty-security multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ jaunty-security multiverse
```I think this may be related to a failed install of Auto-apt, [https://help.ubuntu.com/community/AutoApt](https://help.ubuntu.com/community/AutoApt) 

I was following [the guidelines]("https://help.ubuntu.com/community/CompilingEasyHowTo") on compiling software you see, and it recommended I install it.

When I load up Synaptic I get this:

```
You have 1 broken package on your system!

Use the "Broken" filter to locate it.
```I go to edit >> fix broken packages, and it says "Successfully fixed dependency problems"

But, when I try and install a program....such as emacs, I get

```
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

```Keep in mind, I don't have any other instance of synaptic, apt-get, or add/remove running.


So, can anyone help?

Edit: I also tried switching servers to no avail

EDIT 2: I had to use to killall -w apt-get to get rid of the above error, a new one popped up, and I used 

sudo apt-get clean
sudo apt-get -f install
sudo depmod -a
sudo apt-get update

that seems to have fixed it

Thanks to the smart people on the IRC channel. Hopefully this helps anyone who runs across the same problem

---

### Post by Nisstyre56 on 2009-07-28
I would really appreciate some help with this, I have no clue what to do.

---

