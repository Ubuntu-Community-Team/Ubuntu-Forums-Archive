---
title: "synaptic will not start after CPU swap"
date: 2009-09-29
forum: General Help
---

### Post by stg on 2009-09-29
Working on the hardware here, upgraded from PIII 1.2GHz to PIII-S 1.4GHz tualatin with the 512 cache, best socket 370 CPU ever.  Anyway, system boots, apps run, it folds, all is good except Synaptic package manager will try to start, ask for sudo pwd, then crash away like it was never there.  Same thing with the auto updater, a couple minutes after boot I get a red message icon says "A problem occurred when checking for the updates"

I ran some searches and didn't see anything helpful, anybody have any ideas??

OS is UbuntuStudio 9.04

---

### Post by mac9416 on 2009-09-29
stg, as far as "A problem occurred when checking for the updates" goes, perhaps this may help:

> Open a Terminal from the menu Applications &#8594; Accessories &#8594; Terminal and type:
(when the system ask you a password give your user password, you will not see nothing when you type it, then press enter)

sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get --fix-missing install
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get clean
sudo apt-get autoremove

Please report only error message here if there are any.

I found that here: [https://answers.launchpad.net/ubuntu/+question/55625](https://answers.launchpad.net/ubuntu/+question/55625)

Hope that works!

---

### Post by stg on 2009-09-29
RESOLVED!!

THANK YOU!!


stg@gigtower:~$ sudo dpkg --configure -a
[sudo] password for stg: 
stg@gigtower:~$ sudo apt-get -f install
Reading package lists... Done
Segmentation faulty tree... 50%
stg@gigtower:~$ sudo apt-get --fix-missing install
Reading package lists... Done
Segmentation faulty tree... 50%
stg@gigtower:~$ sudo apt-get clean
stg@gigtower:~$ sudo apt-get update
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release [49.6kB]  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages [183kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages [2589B]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources [52.1kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources [623B]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages [57.3kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources [15.5kB]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages [8128B]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources [2505B]
Fetched 372kB in 3s (105kB/s)                            
Reading package lists... Done
stg@gigtower:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  apport apport-gtk linux-libc-dev python-apport python-problem-report
5 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 1092kB of archives.
After this operation, 4096B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main python-problem-report 1.0-0ubuntu5.4 [72.1kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main python-apport 1.0-0ubuntu5.4 [74.0kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main apport 1.0-0ubuntu5.4 [113kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main apport-gtk 1.0-0ubuntu5.4 [68.0kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main linux-libc-dev 2.6.28-15.52 [765kB]
Fetched 1092kB in 2s (381kB/s)         
(Reading database ... 139893 files and directories currently installed.)
Preparing to replace python-problem-report 1.0-0ubuntu5.2 (using .../python-problem-report_1.0-0ubuntu5.4_all.deb) ...
Unpacking replacement python-problem-report ...
Preparing to replace python-apport 1.0-0ubuntu5.2 (using .../python-apport_1.0-0ubuntu5.4_all.deb) ...
Unpacking replacement python-apport ...
Preparing to replace apport 1.0-0ubuntu5.2 (using .../apport_1.0-0ubuntu5.4_all.deb) ...
 * Stopping automatic crash report generation: apport                    [ OK ] 
Unpacking replacement apport ...
Preparing to replace apport-gtk 1.0-0ubuntu5.2 (using .../apport-gtk_1.0-0ubuntu5.4_all.deb) ...
Unpacking replacement apport-gtk ...
Preparing to replace linux-libc-dev 2.6.28-15.49 (using .../linux-libc-dev_2.6.28-15.52_i386.deb) ...
Unpacking replacement linux-libc-dev ...
Processing triggers for man-db ...
Processing triggers for shared-mime-info ...
Setting up python-problem-report (1.0-0ubuntu5.4) ...

Setting up python-apport (1.0-0ubuntu5.4) ...

Setting up apport (1.0-0ubuntu5.4) ...

Setting up apport-gtk (1.0-0ubuntu5.4) ...

Setting up linux-libc-dev (2.6.28-15.52) ...
stg@gigtower:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
stg@gigtower:~$ sudo apt-get clean
stg@gigtower:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
stg@gigtower:~$

---

### Post by stg on 2009-10-01
uh oh, I spoke too soon.  It updated that time, and then let me run synaptic for a while, but now it is back where it was and...


stg@gigtower:~$ sudo dpkg --configure -a
[sudo] password for stg: 
dpkg: parse error, in file `/var/lib/dpkg/status' near line 24171 package `rarian-compat':
 newline in field name `S'
stg@gigtower:~$ sudo apt-get -f install
Reading package lists... Done
Segmentation faulty tree... 0%
stg@gigtower:~$ sudo apt-get --fix-missing install
Reading package lists... Done
Segmentation faulty tree... 0%
stg@gigtower:~$ sudo apt-get clean
stg@gigtower:~$ sudo apt-get update
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release [49.6kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages [179kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages [2589B]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources [51.7kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources [623B]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages [61.0kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources [16.0kB]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages [8128B]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources [2505B]
Fetched 371kB in 3s (122kB/s)                              
Reading package lists... Error!
E: Malformed 1st word in the Status line
E: Error occurred while processing libglew1.5 (UsePackage2)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
stg@gigtower:~$ sudo apt-get upgrade
Reading package lists... Error!
E: Malformed 1st word in the Status line
E: Error occurred while processing libglew1.5 (UsePackage2)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
stg@gigtower:~$ sudo apt-get dist-upgrade
Reading package lists... Error!
E: Malformed 1st word in the Status line
E: Error occurred while processing libglew1.5 (UsePackage2)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
stg@gigtower:~$ sudo apt-get clean
stg@gigtower:~$ sudo apt-get autoremove
Reading package lists... Error!
E: Malformed 1st word in the Status line
E: Error occurred while processing libglew1.5 (UsePackage2)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
stg@gigtower:~$

---

### Post by stg on 2009-10-01
AAACK!  My source.list is BLANK!! 

HELP!!!

edit, sources.list...duh...OK its not blank


E: Malformed 1st word in the Status line
E: Error occurred while processing libglew1.5 (UsePackage2)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

is the error message, here is my sources.list

# 
# deb cdrom:[Ubuntu-Studio 9.04 _Jaunty Jackalope_ - Release i386 (20090421.4)]/ jaunty main multiverse restricted universe

#deb cdrom:[Ubuntu-Studio 9.04 _Jaunty Jackalope_ - Release i386 (20090421.4)]/ jaunty main multiverse restricted universe
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse

---

### Post by cholericfun on 2009-10-01
when you type 
```
sudo synaptic package manager
```
in the terminal normally Synaptic starts up.
what error messages do you get there?

---

### Post by stg on 2009-10-01
E: Malformed 1st word in the Status line
E: Error occurred while processing libglew1.5 (UsePackage2)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.


thanks, also see edit above

---

### Post by cholericfun on 2009-10-01
heres a sources.list for you
```
# newer versions of the distribution.

deb http://de.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ hardy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://de.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://de.archive.ubuntu.com/ubuntu/ hardy universe
deb http://de.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://de.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://de.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://de.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://de.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
~                                                                                                                                                   
~                                                                                                                                                   
~                                                                                 
```


as you can see this is in hardy, 
i guess you just have to adjust that word..?

> 
thanks, also see edit above

haha,
there should also be a backup.

---

### Post by stg on 2009-10-01
E: Type '~' is not known on line 48 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.


hmm, seems like progress, looking at line 48 now

---

### Post by cholericfun on 2009-10-01
did you use mine? (hardy)
i dont see any ~ in your sources.list
in my copy-paste, some~ got in there accidentally.
but even deleting those would not work and maybe even cause serious damange (dont know though)

---

### Post by stg on 2009-10-01
OMFG!  off topic but this is funny!  I entered "head up butt" in the reason for edit field and it roasted all my beans and says "spilled the beans"

Now that right there is funny!

Yeah, I used yours, missed the hardy comment, not doing so well today, changed it back and it doesn't seem to have broken anything worse.

I need to find a sources.list for my distro or figure out which is the "status line"

Hey, thanks for your help cholericfun!!

---

### Post by cholericfun on 2009-10-01
> "spilled the beans"

that actually is quiet brilliant.
now youre back to 1, you can try out all sort of combinations :)

---

### Post by stg on 2009-10-01
OK, I have located and tried a couple of sources.list files.  If I use a known broken one I get its expected error message.  If I fix it I'm back to

E: Malformed 1st word in the Status line
E: Error occurred while processing libglew1.5 (UsePackage2)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

so I don't think the problem is actually in sources.list

here is the beginning of /var/lib/dpkg/status

Package: gcdmaster
Status: install ok installed
Priority: optional
Section: sound
Installed-Size: 1340
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: cdrdao
Version: 1:1.2.2-17
Depends: libao2 (>= 0.8.8), libart-2.0-2 (>= 2.3.18), libatk1.0-0 (>= 1.20.0), libbonobo2-0 (>= 2.15.0), libbonoboui2-0 (>= 2.15.1), libc6 (>= 2.7), libcairo2 (>= 1.2.4), libcairomm-1.0-1 (>= 1.6.4), libfontconfig1 (>= 2.4.0), libfreetype6 (>= 2.3.5), libgcc1 (>= 1:4.1.1), libgconf2-4 (>= 2.13.5), libgconfmm-2.6-1c2 (>= 2.22.0), libglade2-0 (>= 1:2.6.1), libglademm-2.4-1c2a (>= 2.6.0), libglib2.0-0 (>= 2.12.0), libglibmm-2.4-1c2a (>= 2.18.0), libgnome-vfsmm-2.6-1c2a (>= 2.22.0), libgnome2-0 (>= 2.17.3), libgnomecanvas2-0 (>= 2.11.1), libgnomecanvasmm-2.6-1c2a (>= 2.14.0), libgnomemm-2.6-1c2 (>= 2.16.0), libgnomeui-0 (>= 2.22.0), libgnomeuimm-2.6-1c2a (>= 2.16.0), libgnomevfs2-0 (>= 1:2.17.90), libgtk2.0-0 (>= 2.14.1), libgtkmm-2.4-1c2a (>= 1:2.13.8), libice6 (>= 1:1.0.0), libogg0 (>= 1.0rc3), liborbit2 (>= 1:2.14.10), libpango1.0-0 (>= 1.21.6), libpangomm-1.4-1 (>= 2.14.0), libpopt0 (>= 1.14), libsigc++-2.0-0c2a (>= 2.0.2), libsm6, libstdc++6 (>= 4.2.1), libvorbis0a (>= 1.1.2), libvorbisfile3 (>= 1.1.2), libxml2 (>= 2.6.27), zlib1g (>= 1:1.1.4), cdrdao (= 1:1.2.2-17)

---

### Post by stg on 2009-10-01
Wow, /var/lib/dpkg/status is one big file!  I search for MergeList in it and get no hits.  Sorry I'm such a noob, I'm kind of lost now.

---

### Post by mac9416 on 2009-10-01
stg,

Try this:

```
$ sudo cp /var/lib/dpkg/status /var/lib/dpkg/status.1
$ sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```

---

### Post by stg on 2009-10-01
thanks mac9416 that seems to have got it for now, wonder why the file corrupted?

how old would the backup have been?

---

### Post by mac9416 on 2009-10-01
I really have no idea. You can run this command to see the difference between the backup and the "regular" status file:

```
$ diff /var/lib/dpkg/status-old /var/lib/dpkg/status.1
```

---

