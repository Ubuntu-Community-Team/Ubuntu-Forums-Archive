---
title: "Can't get gnome shell to install"
date: 2012-06-24
forum: General Help
---

### Post by bootbat on 2012-06-24
Hello Experts,

I am trying to install gnome shell but keep getting dependency errors. I tried using some third party PPAs earlier but have since then removed everything and updated my sources list and yet this happens. Here's what I get while trying to install:

```
bootbat@Ubuntu-Home:~$ sudo apt-get install gnome-shell
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gnome-shell : Depends: libmutter0 (< 3.5) but 3.5.2+git20120612.50bc4ad0-0ubuntu1~12.04~ricotz0 is to be installed
               Depends: gnome-shell-common (= 3.4.1-0ubuntu2) but 3.5.2+git20120623.fd62aba7-0ubuntu1~12.04~ricotz0 is to be installed
               Depends: gir1.2-gjsdbus-1.0 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

Any pointers to resolve this will be greatly appreciated.

---

### Post by sgage on 2012-06-24
> **bootbat said:**
> Hello Experts,

I am trying to install gnome shell but keep getting dependency errors. I tried using some third party PPAs earlier but have since then removed everything and updated my sources list and yet this happens. Here's what I get while trying to install:

```
bootbat@Ubuntu-Home:~$ sudo apt-get install gnome-shell
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gnome-shell : Depends: libmutter0 (< 3.5) but 3.5.2+git20120612.50bc4ad0-0ubuntu1~12.04~ricotz0 is to be installed
               Depends: gnome-shell-common (= 3.4.1-0ubuntu2) but 3.5.2+git20120623.fd62aba7-0ubuntu1~12.04~ricotz0 is to be installed
               Depends: gir1.2-gjsdbus-1.0 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

Any pointers to resolve this will be greatly appreciated.

It looks as though your repo lists still point to the ricotz ppa. You may have removed the packages, but you didn't disable/remove the ppa.

---

### Post by bootbat on 2012-06-24
Thanks for your response. 

I thought I disabled/removed all PPA's. Here's the command output for gksudo gedit /etc/apt/sources.list:

```
# deb cdrom:[Ubuntu 12.04 _Precise Pangolin_ - Release i386]/ Precise main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ftp.citylink.co.nz/ubuntu/ precise main restricted
deb-src http://ftp.citylink.co.nz/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ftp.citylink.co.nz/ubuntu/ precise-updates main restricted
deb-src http://ftp.citylink.co.nz/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ftp.citylink.co.nz/ubuntu/ precise universe
deb-src http://ftp.citylink.co.nz/ubuntu/ precise universe
deb http://ftp.citylink.co.nz/ubuntu/ precise-updates universe
deb-src http://ftp.citylink.co.nz/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ftp.citylink.co.nz/ubuntu/ precise multiverse
deb-src http://ftp.citylink.co.nz/ubuntu/ precise multiverse
deb http://ftp.citylink.co.nz/ubuntu/ precise-updates multiverse
deb-src http://ftp.citylink.co.nz/ubuntu/ precise-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ftp.citylink.co.nz/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://ftp.citylink.co.nz/ubuntu/ precise-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner

deb http://ftp.citylink.co.nz/ubuntu/ precise-security main restricted
deb-src http://ftp.citylink.co.nz/ubuntu/ precise-security main restricted
deb http://ftp.citylink.co.nz/ubuntu/ precise-security universe
deb-src http://ftp.citylink.co.nz/ubuntu/ precise-security universe
deb http://ftp.citylink.co.nz/ubuntu/ precise-security multiverse
deb-src http://ftp.citylink.co.nz/ubuntu/ precise-security multiverse

## Medibuntu - Ubuntu 12.04 "Precise Pangolin"
## Please report any bug on https://bugs.launchpad.net/medibuntu/
##deb http://packages.medibuntu.org/ precise free non-free
##deb-src http://packages.medibuntu.org/ precise free non-free

# Google software repository
deb http://dl.google.com/linux/deb/ stable non-free
```

Any ideas what I might be missing?

---

### Post by sgage on 2012-06-24
> **bootbat said:**
> Thanks for your response. 

I thought I disabled/removed all PPA's. Here's the command output for gksudo gedit /etc/apt/sources.list:

```
# deb cdrom:[Ubuntu 12.04 _Precise Pangolin_ - Release i386]/ Precise main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ftp.citylink.co.nz/ubuntu/ precise main restricted
deb-src http://ftp.citylink.co.nz/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ftp.citylink.co.nz/ubuntu/ precise-updates main restricted
deb-src http://ftp.citylink.co.nz/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ftp.citylink.co.nz/ubuntu/ precise universe
deb-src http://ftp.citylink.co.nz/ubuntu/ precise universe
deb http://ftp.citylink.co.nz/ubuntu/ precise-updates universe
deb-src http://ftp.citylink.co.nz/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ftp.citylink.co.nz/ubuntu/ precise multiverse
deb-src http://ftp.citylink.co.nz/ubuntu/ precise multiverse
deb http://ftp.citylink.co.nz/ubuntu/ precise-updates multiverse
deb-src http://ftp.citylink.co.nz/ubuntu/ precise-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ftp.citylink.co.nz/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://ftp.citylink.co.nz/ubuntu/ precise-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner

deb http://ftp.citylink.co.nz/ubuntu/ precise-security main restricted
deb-src http://ftp.citylink.co.nz/ubuntu/ precise-security main restricted
deb http://ftp.citylink.co.nz/ubuntu/ precise-security universe
deb-src http://ftp.citylink.co.nz/ubuntu/ precise-security universe
deb http://ftp.citylink.co.nz/ubuntu/ precise-security multiverse
deb-src http://ftp.citylink.co.nz/ubuntu/ precise-security multiverse

## Medibuntu - Ubuntu 12.04 "Precise Pangolin"
## Please report any bug on https://bugs.launchpad.net/medibuntu/
##deb http://packages.medibuntu.org/ precise free non-free
##deb-src http://packages.medibuntu.org/ precise free non-free

# Google software repository
deb http://dl.google.com/linux/deb/ stable non-free
```

Any ideas what I might be missing?

Look in the directory /etc/apt/sources.list.d and I'll bet you'll find something like ricotz-testing-precise.list (and maybe some others you don't want any more). Just delete it and do the ol' apt-get update and you should be good to go.

If you have Synaptic installed, go to Settings/Repositories/Other Software and easily manage your repos - see which ones you have installed, enable/disable/remove them, etc.

---

### Post by bootbat on 2012-06-24
Thanks for responding again. Not sure what's happening. There were in fact redundant entires in the sources.list.d folder that I removed now. Here are the entires there now:


```
bootbat@Ubuntu-Home:~$ cd /etc/apt/sources.list.d
bootbat@Ubuntu-Home:/etc/apt/sources.list.d$ dir
google-chrome.list	 gwendal-lebihan-dev-cinnamon-stable-precise.list	medibuntu.list
google-chrome.list.save  gwendal-lebihan-dev-cinnamon-stable-precise.list.save	medibuntu.list.save
google-earth.list	 jconti-recent-notifications-precise.list		rye-ubuntuone-extras-precise.list
google-earth.list.save	 jconti-recent-notifications-precise.list.save		rye-ubuntuone-extras-precise.list.save
```

I did a sudo apt-get update without any issues thereafter but when I try to install the gnome shell, I run into the same issues again. Here's what's happening:

```
bootbat@Ubuntu-Home:/etc/apt/sources.list.d$ sudo apt-get install gnome-shell
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gnome-shell : Depends: libmutter0 (< 3.5) but 3.5.2+git20120612.50bc4ad0-0ubuntu1~12.04~ricotz0 is to be installed
               Depends: gnome-shell-common (= 3.4.1-0ubuntu2) but 3.5.2+git20120623.fd62aba7-0ubuntu1~12.04~ricotz0 is to be installed
               Depends: gir1.2-gjsdbus-1.0 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

Sorry but I am going to have to ask for some more help. Appreciate anything that you can point to.

---

### Post by sgage on 2012-06-24
apt-get clearly is finding some ricotz ppa and is getting confused.

If I were you, I'd install Synaptic (sudo apt-get install synaptic) and go to Settings/Repositories/Other Software and have a look at what's there.

Synaptic can be a very useful tool for visualizing what's going on. It's the first thing I install after a fresh Ubuntu installation.

You can filter for "installed" packages, and search for gnome-shell, and you might get some clues. 

In future, if you ever use a ppa and decide you don't want to any more, always use ppa-purge to delete it - it will "downgrade" everything back to the versions in the stock repos.

---

### Post by bootbat on 2012-06-24
Thanks again for responding. I actually have synaptic installed. I used the custom filters to look for anything broken but it draws blank. I have attached a screenshot of my sources list from synaptic for your reference.

Another thing that I noticed - I do not have gnome shell installed but another package named "gnome-shell-common" installed. Not sure if I am making sense at all. I am attaching another screenshot for your reference.

---

### Post by sgage on 2012-06-24
> **bootbat said:**
> Thanks again for responding. I actually have synaptic installed. I used the custom filters to look for anything broken but it draws blank. I have attached a screenshot of my sources list from synaptic for your reference.

Another thing that I noticed - I do not have gnome shell installed but another package named "gnome-shell-common" installed. Not sure if I am making sense at all. I am attaching another screenshot for your reference.

Purge gnome-shell-common (what version is it?). In fact, if I were you, I'd go into Synaptic, click on the Status button, and see if there are any "auto-removable" packages - if so, I'd purge them. Then, still in Status mode, click the "installed" item,  put gnome-shell in the searchbox, and purge anything that comes up. (Synaptic will tell you what it's about to do, so if something critical seems to be about to go, you can reconsider.) 

BTW, I can't open your screenshots - xcf?

---

### Post by sgage on 2012-06-24
I've looked at your screenshots (figured out they were Gimp files). Looks like gnome-shell-common was from ricotz, which is probably your problem.

Purge that bad boy and try again. You might want to disable jconti as well, just until you get GS installed. I'm assuming that what you're trying to accomplish is getting the stock GS 3.4 installed from the official Ubuntu repos...

---

### Post by bootbat on 2012-06-24
Thanks to you, I have been able to purge all the bad PPAs and install the gnome shell. I was trying to move away from the Unity environment and move to Gnome 3. I am running:

```
bootbat@Ubuntu-Home:~$ gnome-session --version
gnome-session 3.2.1
```

Is there anything needed apart from the gnome shell to move to the GNOME 3 environment?

---

### Post by bootbat on 2012-06-24
> I'm assuming that what you're trying to accomplish is getting the stock GS 3.4 installed from the official Ubuntu repos...

Yes, you are right. Still no luck:-(

---

### Post by sgage on 2012-06-24
> **bootbat said:**
> Yes, you are right. Still no luck:-(

You are running Precise (12.04)? Was this a clean install or an upgrade from an earlier version? Start up System Monitor, go to the System tab, and what do you see under Ubuntu?

---

### Post by bootbat on 2012-06-24
This was a clean install about the same time Precise was launched. Under the System Monitor, here's what I see:

> Release 12.04 (precise) 32-bit
Kernel Linux 3.2.0-25-generic-pae
GNOME 3.4.1

I guess I have GS now but I did something incredibly stupid while trying to fix this. I must have uninstalled something that has now handed me into Unity 2D without a way to get into Unity 3D. 

> bootbat@Ubuntu-Home:~$ echo $DESKTOP_SESSION
ubuntu-2d

Everything bloated:-(..Tried restarting and I do not get the normal login. It's a weird login screen. Not sure what this is. When I get into the gnome shell login prompt, it again gives me weird fonts - something like a display issue. Any ideas?

---

### Post by sgage on 2012-06-24
> **bootbat said:**
> This was a clean install about the same time Precise was launched. Under the System Monitor, here's what I see:



I guess I have GS now but I did something incredibly stupid while trying to fix this. I must have uninstalled something that has now handed me into Unity 2D without a way to get into Unity 3D. 



Everything bloated:-(..Tried restarting and I do not get the normal login. It's a weird login screen. Not sure what this is. When I get into the gnome shell login prompt, it again gives me weird fonts - something like a display issue. Any ideas?

Wow, hard to know what's going on. What graphics card do you have? It might be as simple as reinstalling the drivers.

Or, you might have worked yourself into one of those situations where it would be easiest to reinstall - Probably could have reinstalled 5 or 6 times in the time we've been discussing this.  :KS

---

### Post by bootbat on 2012-07-02
Thanks! 

I decided to go ahead and do a clean install again. Issue Resolved:-) Thank you again for helping me find a solution to the issue.

---

