---
title: "Could not download all repository indexes"
date: 2010-03-31
forum: General Help
---

### Post by ishan28mkip on 2010-03-31
I have recently installed ubuntu and evrey time I try installing some new application or updating the computer I get this error:

**[COLOR=Black]Could not download all repository indexes[/COLOR]**
The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

The method driver /usr/lib/apt/methods/htttp could not be found.The method driver /usr/lib/apt/methods/htttp could not be found.

I have tried searching the matter on google without any avail. I was very excited about using but now all hopes seem down.

Please Provide me a clear solution.
Thanks

---

### Post by plucky on 2010-03-31
Welcome to the forum.

Are you able to connect to the internet from Ubuntu?

If you are then:-

Open a terminal window **Applications > Accessories > Terminal** and type in this command ```
sudo apt-get update
``` and if possible post the output to the forum.It will ask for your password,which it won't echo,just type it in and press enter.

Also again from a terminal ```
cat /etc/apt/sources.list
``` and again post to the forum.

Good Luck

---

### Post by ishan28mkip on 2010-04-01
I wrote the two codes and these were the results.

ishan@ishan-desktop:~$ sudo apt-get update
E: The method driver /usr/lib/apt/methods/htttp could not be found.
E: The method driver /usr/lib/apt/methods/htttp could not be found.


ishan@ishan-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ftp.iitm.ac.in/ubuntu/](http://ftp.iitm.ac.in/ubuntu/) karmic main restricted
deb-src [http://ftp.iitm.ac.in/ubuntu/](http://ftp.iitm.ac.in/ubuntu/) karmic restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ftp.iitm.ac.in/ubuntu/](http://ftp.iitm.ac.in/ubuntu/) karmic-updates main restricted
deb-src [http://ftp.iitm.ac.in/ubuntu/](http://ftp.iitm.ac.in/ubuntu/) karmic-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ftp.iitm.ac.in/ubuntu/](http://ftp.iitm.ac.in/ubuntu/) karmic universe
deb [http://ftp.iitm.ac.in/ubuntu/](http://ftp.iitm.ac.in/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ftp.iitm.ac.in/ubuntu/](http://ftp.iitm.ac.in/ubuntu/) karmic multiverse
deb [http://ftp.iitm.ac.in/ubuntu/](http://ftp.iitm.ac.in/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://ftp.iitm.ac.in/ubuntu/](http://ftp.iitm.ac.in/ubuntu/) karmic-security main restricted
deb-src [http://ftp.iitm.ac.in/ubuntu/](http://ftp.iitm.ac.in/ubuntu/) karmic-security restricted main multiverse universe #Added by software-properties
deb [http://ftp.iitm.ac.in/ubuntu/](http://ftp.iitm.ac.in/ubuntu/) karmic-security universe
deb [http://ftp.iitm.ac.in/ubuntu/](http://ftp.iitm.ac.in/ubuntu/) karmic-security multiverse
deb htttp://ftp.debian.org sarge main

ishan@ishan-desktop:~$

---

### Post by plucky on 2010-04-01
> deb htttp://ftp.debian.org sarge main

I don't think it should have 3 ts' in http.Also I don't think you should mix repositories.Not everything in the debian repository will work in Ubuntu.But again that is your choice.

To edit that file ```
gksudo gedit /etc/apt/sources.list
``` and remove the t or to remove the repository, put a # in front of the line.

Like ```
#deb htttp://ftp.debian.org sarge main
```

Good Luck

---

