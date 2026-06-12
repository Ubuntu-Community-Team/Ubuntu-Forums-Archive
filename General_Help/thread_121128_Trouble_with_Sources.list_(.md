---
title: "Trouble with Sources.list :("
date: 2006-01-24
forum: General Help
---

### Post by wizzkid on 2006-01-24
I had some trouble in my sources.list, I cp sources.list to sources.list.bak, and updated some repositories following this link [http://ubuntuguide.squarecows.com/doku.php](http://ubuntuguide.squarecows.com/doku.php)  after updating and intsalling the gstreamer plugins, i copy back the original sources which is sources.list.bak cp to souces.list. now when I type sudo apt-get update, i receive this message. its the cdrom repositories, my cdrom repository is deb cdrom:[Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted 


ERROR MESSAGES:
~$ sudo apt-get update
Ign cdrom://Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy Release.gpg
Ign cdrom://Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy Release
Ign cdrom://Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages
Ign cdrom://Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages
Err cdrom://Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
get1.......
get2.....
hit.......
hit.......
Fetched 5B in 3s (1B/s)
Failed to fetch cdrom:[Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/dists/breezy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/dists/breezy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Reading package lists... Done
W: Couldn't stat source package list cdrom://Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages (/var/lib/apt/lists/Kubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Kubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

Does anybody knows how to fix this problem? :

---

### Post by Jucato on 2006-01-24
I'm not sure, but shouldn't the cdrom repository be disabled after installation since it's practically useless/outdated? Also, why did you copy back the original sources_list after updating? It might cause some package conflicts when you try to update/upgrade again.

---

### Post by Jucato on 2006-01-24
EDIT: Sorry for the double post, my Konq messed up a bit.

---

### Post by mips on 2006-01-24
Don't worry you are not the only one, join the club:
[http://ubuntuforums.org/showthread.php?t=120621](http://ubuntuforums.org/showthread.php?t=120621)

---

### Post by wizzkid on 2006-01-24
I copied back the orginal sources list because, Im affraid it messed my OS, like sort of bad software and that. I just wanted to download the movie plugins.

---

### Post by wizzkid on 2006-01-24
HI, I just wonder if its safe to add new repo in my sources.list. can you guys post your sources.list here so I could compare.. my repo is:

#deb cdrom:[Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted 

deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) breezy main restricted 
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) breezy main restricted 

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) breezy-updates main restricted 
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) breezy-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) breezy universe 
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) breezy universe 

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) breezy-backports main restricted universe multiverse 
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) breezy-backports main restricted universe multiverse 

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security main restricted 

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security universe 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security universe 

#KDE 3.5
deb [http://kubuntu.org/packages/kde35/](http://kubuntu.org/packages/kde35/) breezy main 


Thanks a lot

---

### Post by Jucato on 2006-01-24
I think you won't mess it up too much, except that older repos might cause some conflicts with newer packages. Anyhow, you shouldn't be putting repos from sources you don't trust, usually those not endoresed by Ubuntu or by stickied threads in these forums. So far I haven't found any trouble, even if I have added/deleted/disabled some repos.

Here's my sources.list. I've deleted the cdrom repos immediately after installing and before upgrading my kernel and KDE, coz the cd will always contain either the older or the current versions of packages only.

```
# deb http://kubuntu.org/packages/amarok-1.3.8 breezy main 
# deb http://kubuntu.org/packages/kde35 breezy main 
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted 

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted 
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src http://archive.ubuntu.com/ubuntu breezy universe 

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
## deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted 
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted 

deb http://security.ubuntu.com/ubuntu breezy-security universe 
deb-src http://security.ubuntu.com/ubuntu breezy-security universe 

deb http://archive.ubuntu.com/ubuntu/ breezy universe main restricted multiverse 

# deb http://wine.sourceforge.net/apt/ binary / 

# deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free 
# deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free 

# deb http://deb.opera.com/opera/ etch non-free 

deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse 

## created by arniekde35

```

btw, after you  disabled the cdrom, did your update and upgrade go on well?

---

### Post by Neo Ex on 2006-01-25
Insert the Kubuntu CD-Rom and run
sudo apt-cdrom /dev/hdc (or the device in that you've inserted the disk)
Then sudo apt-get update will work.
This happen when you remove/comment the first line of your sources.list, or if you have changed the sources.list to an another that hasn't the Kubuntu CD-Rom in the sources.

---

