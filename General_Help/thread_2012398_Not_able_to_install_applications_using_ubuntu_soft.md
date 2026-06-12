---
title: "Not able to install applications using ubuntu software center"
date: 2012-06-29
forum: General Help
---

### Post by madhangc on 2012-06-29
Hi,

I am facing the error below on my Ubuntu Software Center when I try to use it:

---------------------------------------

installArchives() failed: dpkg: error processing libk5crypto3:i386 (--configure): 
 libk5crypto3:i386 1.10+dfsg~beta1-2 cannot be configured because libk5crypto3:amd64 is in a different version (1.10+dfsg~beta1-2ubuntu0.1) 
dpkg: error processing libk5crypto3 (--configure): 
 libk5crypto3:amd64 1.10+dfsg~beta1-2ubuntu0.1 cannot be configured because libk5crypto3:i386 is in a different version (1.10+dfsg~beta1-2) 
No apport report written because MaxReports is reached already
Errors were encountered while processing: 
 libk5crypto3:i386 
 libk5crypto3 
Error in function:  
dpkg: error processing libk5crypto3 (--configure): 
 libk5crypto3:amd64 1.10+dfsg~beta1-2ubuntu0.1 cannot be configured because libk5crypto3:i386 is in a different version (1.10+dfsg~beta1-2) 
dpkg: error processing libk5crypto3:i386 (--configure): 
 libk5crypto3:i386 1.10+dfsg~beta1-2 cannot be configured because libk5crypto3:amd64 is in a different version (1.10+dfsg~beta1-2ubuntu0.1) 

---------------------------------------------

Even Synaptic Package Manager says there is an error. Any ideas how can i fix this. Thanks in advance.

---

### Post by hunter.allen on 2012-07-02
Hm... 

You seem to be having some package conflicts. The packages you are installing have both the i386 and amd64 architecture. You seem to be using some sources that are outdated (maybe upgrading your ubuntu distribution?). 

Regardless of the problems orgin, please post your /etc/apt/sources.list file:

```
gedit /etc/apt/sources.list

```

Then paste the text in the forum. 

I can provide further help after you post. It would also be of use to see the packages' respective origins.

---

### Post by madhangc on 2012-07-03
> **hunter.allen said:**
> Hm... 

You seem to be having some package conflicts. The packages you are installing have both the i386 and amd64 architecture. You seem to be using some sources that are outdated (maybe upgrading your ubuntu distribution?). 

Regardless of the problems orgin, please post your /etc/apt/sources.list file:

```
gedit /etc/apt/sources.list

```Then paste the text in the forum. 

I can provide further help after you post. It would also be of use to see the packages' respective origins.

Hi Allen,

Thanks for your response. Here is the content from the sources.list file:

----------------------------------------------------

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise universe
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

----------------------------------------------------------

I really appreciate your help on this matter. Thanks again.

---

### Post by hunter.allen on 2012-07-03
Ok. So it's not your sources. 

Things to try: 
- Update software database
- Remove packages that already exist with this name

It seems you like beta versions. If you have a version installed, try removing it before installing these. 

Are you installing this software from a .deb file? That changes things entirely if you are...

---

### Post by jmfal on 2012-07-03
Try this then update/upgrade

```
  sudo dpkg --configure  -a        
```

If it doesn't do anything you might need to run "dpkg" while in the recovery kernal and run the command at the command prompt.

---

### Post by madhangc on 2012-07-04
Thank you guys for all your help. I just used synaptic manager to removed the problematic packages and things and the error is gone.  Along with them some of the packages got removed. But none of the removed packages looked like I needed them. 

I think this issue is fixed and I will get back to you if I face more issues. 

Thanks again for all your help. 

Best Regards,
-Madhan

---

