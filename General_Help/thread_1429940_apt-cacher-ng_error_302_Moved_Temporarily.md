---
title: "apt-cacher-ng error: 302 Moved Temporarily"
date: 2010-03-14
forum: General Help
---

### Post by owenspa on 2010-03-14
I've been attempting to install Virtualbox 3.1 on my desktop
using the "Add and Remove Software" facility.  All attempts
result in failure with the "Details" error message box issuing

> Failed to fetch [http://download.virtualbox.org/virtualbox/debian/pool/non-free/v/virtualbox-3.1/virtualbox-3.1_3.1.4-57640_Ubuntu_karmic_i386.deb](http://download.virtualbox.org/virtualbox/debian/pool/non-free/v/virtualbox-3.1/virtualbox-3.1_3.1.4-57640_Ubuntu_karmic_i386.deb) 302 Moved Temporarily [IP: ::1 3142]

I have recently freshly installing *Karmic* and *apt-cacher-ng* after
a disk crash. I was running *Hardy* and *apt-cacher* previously.

I successfully installed Virtualbox 3.1 on my laptop through
*apt-cacher-ng* on the desktop machine.  However, I now realise
that I had neglected to change the entries in **/etc/apt/sources.list**
on my laptop from

> deb [http://desk:3142/download.virtual](http://desk:3142/download.virtual)....

to

> deb [http://download.virtual](http://download.virtual)....

and install the **02proxy** file in **/etc/apt/apt.conf.d** on the laptop

I've run through the manual "Scan and/or Expiration" procedure at
```
http://localhost:3142/acng-report.html
```
to no avail.

I've waited for over a week hoping that the fault was at the repository,
but there's been no change.

I've been able to install other packages and do updates on the desktop
and other machine without problems.

What can I do to fix this problem?

---

### Post by bobcollard on 2010-03-14
You can run the following to change the first problem and save it.
```
sudo gedit /etc/apt/sources.list
```Then run: 
```
sudo gedit /etc/apt/apt.conf.d
``` for the proxy code.  If you get an error telling you to install gedit,  then follow the instructions for that.  Also check your System/Software Sources to make sure the repositories are checked.

---

### Post by owenspa on 2010-03-14
> **bobcollard said:**
> You can run the following to change the first problem and save it.
```
sudo gedit /etc/apt/sources.list
```Then run: 
```
sudo gedit /etc/apt/apt.conf.d
``` for the proxy code.  If you get an error telling you to install gedit,  then follow the instructions for that.  Also check your System/Software Sources to make sure the repositories are checked.

Sorry, but I can't fathom the reasoning behind your instructions.
I use "vi" for text editing, and I don't want to have to install
the plethora of gnome run time libraries to install "gedit".
Does "gedit" provide context editing of "sources.list" files?
Why edit the "apt.conf.d" directory?

My /etc/apt/sources.list file -

> # deb cdrom:[Kubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted                                                                   
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to       
# newer versions of the distribution.                                           

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.                                                
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any  
## review or updates from the Ubuntu security team.                        
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic universe                   
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic universe               
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic-updates universe           
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic-updates universe       

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) karmic non-free

my /etc/apt/apt.conf.d/02proxy file:

> Acquire::http { Proxy "http://localhost:3142"; };


Thanks.

---

### Post by bobcollard on 2010-03-15
> install the **02proxy** file in **/etc/apt/apt.conf.d** on the laptop
Your words.  If you have a better way to get to those files to edit them, you can do it that way.  If this were Kubuntu I'd have suggested:
```
kdesudo kate /etc/apt/apt.conf.d
```

---

### Post by owenspa on 2010-03-15
My apologies bobcollard, I did not make myself clear in the
original post.  The sequence of events was this

I use kubuntu.

I had my desktop running hardy and apt-cacher.
My laptop was running karmic and doing upgrades
and installs through apt-cacher on the desktop.
To do this I had modified /etc/apt/sources.list
on the laptop so all entries used
> [http://desk:3142/](http://desk:3142/)......
The disk on the desktop machine crashed to I took
the opportunity upgrade it to karmic and apt-cacher-ng.

BTW, I did not preload the new karmic/apt-cacher-ng system
with the cache from the old hardy/apt-cacher system.

Without making any changes to the laptop I installed
virtualbox 3.1 on the laptop.

I have since read that this can cause problems and
made the appropriate changes to /etc/apt/sources.list
and created an appropriate /etc/apt/apt.conf.d/02proxy
file on the laptop.

But now, all attempts to install virtualbox 3.1 on the
desktop result in the error as described in my original
post.

---

### Post by lykwydchykyn on 2010-03-15
if you temporarily comment out the proxy configuration, does it work?

That would at least tell you if the proxy was the problem.

I recently set apt-cacher-ng up at home myself, but I haven't had this problem (and I use virtualbox), so in theory it should work.

---

### Post by owenspa on 2010-03-15
The proxy has worked for all other packages and updates on the proxy
server (desktop).  Its just this one package which happens to be the
one package I installed on the laptop when its configuration to
use the proxy was not as recommended.

---

### Post by owenspa on 2010-03-15
I just successfully downloaded the ".deb" file as specified in the error
message.  So its not the repository.

Another question: is it OK to install this ".deb" file and ignore
the message advising to install through the software channel instead?

I'm concerned that If I don't fix the original problem its going
to bite again and possibly harder later.

---

### Post by lykwydchykyn on 2010-03-16
> **owenspa said:**
> The proxy has worked for all other packages and updates on the proxy
server (desktop).  Its just this one package which happens to be the
one package I installed on the laptop when its configuration to
use the proxy was not as recommended.
Silly question, but I must ask; you've done an "apt-get update" since changing, right?


> **owenspa said:**
> I just successfully downloaded the ".deb" file as specified in the error
message.  So its not the repository.

Another question: is it OK to install this ".deb" file and ignore
the message advising to install through the software channel instead?

I'm concerned that If I don't fix the original problem its going
to bite again and possibly harder later.

There's no real difference in the end.  The only thing extra you might get from apt is dependency handling and (of course) caching, but I don't know that either will be significant in this case.

---

### Post by owenspa on 2010-03-16
> Silly question, but I must ask; you've done an "apt-get update" since changing, right?
Yep, many times.

---

### Post by undecidable on 2010-03-25
The problem appears to be the virtualbox repo is suddenly using "redirect"  feature that Deb does not yet support.  cf

  [http://forums.virtualbox.org/viewtopic.php?f=7&t=28581](http://forums.virtualbox.org/viewtopic.php?f=7&t=28581)


I am having the same problem in Kubuntu 8.04, everything standard.  

Only solution I have seen proposed is to uninstall / re-install from the .deb rather than the repos.  Seems like a bad idea.   Plus I m not sure how that helps when the next update is required.

mc

---

