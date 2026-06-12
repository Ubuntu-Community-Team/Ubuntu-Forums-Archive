---
title: "cannot update any which way"
date: 2011-03-19
forum: General Help
---

### Post by dazndom on 2011-03-19
i cannot get updates thru terminal or synaptic, in fact update manager and and synaptic dont even open properly they just come up with the same error message.

here is copy of terminal;
darren@darren-desktop:~$ sudo apt-get install update
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_maverick-updates_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

and here is synaptic error message;

Could not initialize the package information

An unresolvable problem occurred while initialising the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_maverick-updates_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

Any ideas

cheers Daz

---

### Post by andrewthomas on 2011-03-19
> **dazndom said:**
> 
E: Problem with MergeList /var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_maverick-updates_main_binary-i386_Packages

Any ideas


Either temporarily disable the maverick-updates repo in your sources.list

or 

temporarily switch from au.archive.ubuntu.com to the main server.

---

### Post by blueridgedog on 2011-03-19
To disable a source, System > Administration > Update Manager, then settings to get to the location of your sources.

---

### Post by dazndom on 2011-03-19
i cannot open synaptic  or update manager.

the above error message opens before synaptic is fully open and when i close the error dialogue box both programs close immediately

any other ideas?????

i donot have a software sources app under system/ admininstration

i cannot open ubuntu software centre as it just seems to crash

again here is the error message;

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_maverick-updates_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'


cheers Daz

---

### Post by andrewthomas on 2011-03-19
Don't open synaptic or update manager.  

In a terminal:

```
sudo apt-get update && sudo apt-get upgrade
```

and post any errors.

---

### Post by dazndom on 2011-03-19
darren@darren-desktop:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for darren: 
0% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting f

this is after 10 mins.

infact now that i think about it, ever since last upgrade from 10.04 - 10.10
i have had this problem with headers

i think i have put sources to MAIN SERVER  when it was on Australia

my first post said i cannot get  "sudo apt-get install update"

cheers Daz

---

### Post by blueridgedog on 2011-03-19
What is the contents of our sources list?

```
cat /etc/apt/sources.list
```

---

### Post by dazndom on 2011-03-19
darren@darren-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) maverick universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) maverick-updates universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) maverick multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main #Third party developers repository
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) maverick-backports restricted main multiverse universe
darren@darren-desktop:~$

---

### Post by dazndom on 2011-03-20
> **andrewthomas said:**
> Don't open synaptic or update manager.  

In a terminal:

```
sudo apt-get update && sudo apt-get upgrade
```and post any errors.


on top staus bar there is a red circcle with white line thru it which is synaptic warning/failure/error msg....
well i just RIGHT clicked it and a menu came up and i could open preferences/source
i unticked backports on both tabs it is in

in terminal ran sudo apt-get update

here is result of that;

Fetched 8,269kB in 8min 47s (15.7kB/s)                                         
Reading package lists... Done
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_maverick_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
darren@darren-desktop:~$ 


then ran sudo apt-get upgrade

here is result;

no errors 

does that mean im fixed
 will go and do it again with backports in it

---

### Post by blueridgedog on 2011-03-20
> **dazndom said:**
> 
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner i386 

Strange, as your sources list has only one entry.

---

### Post by dazndom on 2011-03-20
so i went back and enable back ports and then checked updates and it told me to do a partial upgrade and it had linux kernal 2.6.35-28 stuff in it
. it has done this successfully and i am about to reboot 

back soon

---

### Post by dazndom on 2011-03-20
all seems good

ran update all good no more to do

thanks to all


but do i need to worry ??????

---

### Post by r94851486 on 2011-04-02
Hi.. :) i got solution...
Actually, just fixed the problem using:

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

---

