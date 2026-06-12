---
title: "Update Manager problem today"
date: 2010-10-20
forum: General Help
---

### Post by Scunnered on 2010-10-20
When I accepted the update today I was asked to load my 10.10 disk which I did only to have the report that it was not found. Very strange.

I currently am using 10.04 but did load 10.10 on a Virtualbox so am at a loss why I was being asked for a disk.  This was done primarly as the system would not properly display on my laptop as it shrunk the view by about one inch on both the left and right hand side of the screen.

At the end of the download there was report of the changes applied during the update which I attach for information.

Can anyone offer any assistance / guidance on these problems?

---

### Post by plucky on 2010-10-20
> Can anyone offer any assistance / guidance on these problems? 


Post your sources.list ```
cat /etc/apt/sources.list
```

Or Open Software Sources and un-tick the CDrom as a source and delete it.

It was probably added accidentally when you had it mounted to use for Virtualbox.


Good Luck

---

### Post by Scunnered on 2010-10-20
Many thanks for your reply

Details are as follows:


ian@ian-laptop:~$ cat /etc/apt/sources.list
#deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse

ian@ian-laptop:~$ 

I hope this makes sense to you as it is double Dutch to me !

Looking forward to your reply

---

### Post by plucky on 2010-10-20
> deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted

That is the line you should put a # in front of so it looks like ```
#deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
```

Either 
Open **System > Administration > Software Sources** and un-tick the box that mentions "Maverick"

Or

From a terminal ```
gksudo gedit /etc/apt/sources.list
``` and put a # in front of the line that mentions the Maverick CDrom.

Then run ```
sudo apt-get update
```

Good Luck

---

### Post by welshmike on 2010-10-20
I accepted to update from update manager today and was surprised how large the update was and the long time of about 15 minutes or more to download (at 5 mbps) and install the changes.
Did anyone else have this experience?

---

### Post by plucky on 2010-10-20
> **welshmike said:**
> I accepted to update from update manager today and was surprised how large the update was and the long time of about 15 minutes or more to download (at 5 mbps) and install the changes.
Did anyone else have this experience?

My download speed was 37-45 kB/s instead of the normal 491 kB/s and a total of 71Mb to update.

5 Mb/s connection.The canonical servers are probably being hammered.

Good Luck

---

### Post by Scunnered on 2010-10-20
Again my thanks to you for all your kind assistance.

Like you I found that this mornings update was slower than usual but I put it down to the error messages.  Checking now following the instructions I am now fully up to speed.

Anyone have any idea on the display problem or how I may best address it?

---

