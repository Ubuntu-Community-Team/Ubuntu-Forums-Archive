---
title: "Problem installing webmin"
date: 2010-03-03
forum: General Help
---

### Post by Kwaka on 2010-03-03
I've been scratching my head on this one for a while.
My level of knowledge of Linux isn't great. I know enough to be dangerous. :D
I'm trying to get Webmin installed to give me an easier web front to Linux. 
I run the command to get the prereq's.
> 
sudo apt-get install perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl libmd5-perl
Reading package lists... Done
Building dependency tree
Reading state information... Done
perl is already the newest version.
E: Couldn't find package libnet-ssleay-perl
So I can see that it can't find libnet-ssleay-perl

I bit of searching around leads me to the sources.list file which tells apt-get where to get the packages I think.

THis is as follows.

> #
# deb cdrom:[Ubuntu-Server 8.04 _Hardy Heron_ - Release amd64 (20080423.2)]/ hardy main restricted

#deb cdrom:[Ubuntu-Server 8.04 _Hardy Heron_ - Release amd64 (20080423.2)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://update.onlinehome-server.info/ubuntu/](http://update.onlinehome-server.info/ubuntu/) hardy main restricted
deb-src [http://update.onlinehome-server.info/ubuntu/](http://update.onlinehome-server.info/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://update.onlinehome-server.info/ubuntu/](http://update.onlinehome-server.info/ubuntu/) hardy-updates main restricted
deb-src [http://update.onlinehome-server.info/ubuntu/](http://update.onlinehome-server.info/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://update.onlinehome-server.info/ubuntu/](http://update.onlinehome-server.info/ubuntu/) hardy universe
deb-src [http://update.onlinehome-server.info/ubuntu/](http://update.onlinehome-server.info/ubuntu/) hardy universe
deb [http://update.onlinehome-server.info/ubuntu/](http://update.onlinehome-server.info/ubuntu/) hardy-updates universe
deb-src [http://update.onlinehome-server.info/ubuntu/](http://update.onlinehome-server.info/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://update.onlinehome-server.info/ubuntu/](http://update.onlinehome-server.info/ubuntu/) hardy multiverse
deb-src [http://update.onlinehome-server.info/ubuntu/](http://update.onlinehome-server.info/ubuntu/) hardy multiverse
deb [http://update.onlinehome-server.info/ubuntu/](http://update.onlinehome-server.info/ubuntu/) hardy-updates multiverse
deb-src [http://update.onlinehome-server.info/ubuntu/](http://update.onlinehome-server.info/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://update.onlinehome-server.info/ubuntu/](http://update.onlinehome-server.info/ubuntu/) hardy-backports main restricted universe multiverse
deb-src [http://update.onlinehome-server.info/ubuntu/](http://update.onlinehome-server.info/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://update.onlinehome-server.info/ubuntu/](http://update.onlinehome-server.info/ubuntu/) hardy-security main restricted
deb-src [http://update.onlinehome-server.info/ubuntu/](http://update.onlinehome-server.info/ubuntu/) hardy-security main restricted
deb [http://update.onlinehome-server.info/ubuntu/](http://update.onlinehome-server.info/ubuntu/) hardy-security universe
deb-src [http://update.onlinehome-server.info/ubuntu/](http://update.onlinehome-server.info/ubuntu/) hardy-security universe
deb [http://update.onlinehome-server.info/ubuntu/](http://update.onlinehome-server.info/ubuntu/) hardy-security multiverse
deb-src [http://update.onlinehome-server.info/ubuntu/](http://update.onlinehome-server.info/ubuntu/) hardy-security multiverse
I've uncommented the multiverse and parner lines as I read somewhere that this might help, but I'm still stumped.

Can anyone help me.
TIA
Dave

---

### Post by Kwaka on 2010-03-03
Well I'm getting really confused by this...

I've changed the URL's in the sources.list over to the following.

> 
#
# deb cdrom:[Ubuntu-Server 8.04 _Hardy Heron_ - Release amd64 (20080423.2)]/ hardy main restricted

#deb cdrom:[Ubuntu-Server 8.04 _Hardy Heron_ - Release amd64 (20080423.2)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security universe
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security multiverse
deb-src [http://update.onlinehome-server.info/ubuntu/](http://update.onlinehome-server.info/ubuntu/) hardy-security multiverse


Still no joy then. How on earth can I get the libnet-ssleay-perl library installed???
Please help someone! :-)

---

### Post by Kwaka on 2010-03-03
Sorted I just needed to run "apt-get update" after I'd changed the sources.list file.
Hmmmm something so simple but has taken me hours to sort.
Ahh well.
Webmin running nicely now.

---

### Post by lisati on 2010-03-03
> **Kwaka said:**
> Sorted I just needed to run "apt-get update" after I'd changed the sources.list file.
Hmmmm something so simple but has taken me hours to sort.
Ahh well.
Webmin running nicely now.

Good to hear that you worked it out. I use webmin too, and generally have a tab open on my laptop so I can monitor my server while browsing.

---

### Post by Kwaka on 2010-03-03
> **lisati said:**
> Good to hear that you worked it out. I use webmin too, and generally have a tab open on my laptop so I can monitor my server while browsing.

I have a cloud server from 1and1 which came with Plesk. I hate it!
So vaped and replaced with Ubuntu and Webmin. Now I'm at home and can do what I want.

---

