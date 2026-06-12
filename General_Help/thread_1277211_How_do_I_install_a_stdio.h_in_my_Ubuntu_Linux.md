---
title: "How do I install a stdio.h in my Ubuntu Linux?"
date: 2009-09-28
forum: General Help
---

### Post by xvkkd on 2009-09-28
My Ubuntu Debian type of Linux does not contain the "stdio.h" file. As a result, I cannot even compile the simplest of C programs.

All I got when I compile my program was "error: stdio.h: No such file or directory"

When I typed "sudo apt-get install build-essential", my terminal said:  "E: Couldn't find package build-essential."  So I still can't install the stdio.h.

Does anyone know how can I install the stdio.h file into my Ubuntu Linux? Can anyone kindly explain to me in the simplest terms? Thanks in advance.

---

### Post by lloyd_b on 2009-09-28
> **xvkkd said:**
> My Ubuntu Debian type of Linux does not contain the "stdio.h" file. As a result, I cannot even compile the simplest of C programs.

All I got when I compile my program was "error: stdio.h: No such file or directory"

When I typed "sudo apt-get install build-essential", my terminal said:  "E: Couldn't find package build-essential."  So I still can't install the stdio.h.

Does anyone know how can I install the stdio.h file into my Ubuntu Linux? Can anyone kindly explain to me in the simplest terms? Thanks in advance.

First off, could you clarify exactly which Linux distro you are using?  Ubuntu is a derivative of Debian, so they have a lot in common, but there are a few differences.

Regardless of which you're actually running, the "build-essential" package *should* be there - it's common to both Ubuntu and Debian.

Try this: "sudo apt-get install libc6-dev" - this will install *just* the standard include files (such as stdio.h).  But don't be surprised if you still have other problems afterward.  It sounds like you have an incomplete build system installed, and that can cause all sorts of issues.

Lloyd B.

Edit: Just to make sure you have complete package lists, try running "sudo apt-get update", and see if that gets any errors.  If that runs and appears to be fetching updated package lists, then try the "sudo apt-get build-essential"

---

### Post by xvkkd on 2009-09-29
Thank you lloyd_b.

However, when I typed in "sudo apt-get install libc6-dev" as you suggested, all I got was this.

"Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libc6-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libc6-dev has no installation candidate"

It seems the stdio.h is still somehow not installed. 

So what is the problem now and what can I do? Thanks.

---

### Post by undecim on 2009-09-29
Is your package list up to date?

sudo apt-get update

---

### Post by lloyd_b on 2009-09-29
> **xvkkd said:**
> Thank you lloyd_b.

However, when I typed in "sudo apt-get install libc6-dev" as you suggested, all I got was this.

"Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libc6-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libc6-dev has no installation candidate"

It seems the stdio.h is still somehow not installed. 

So what is the problem now and what can I do? Thanks.

Something is wrong with Apt.  Run "sudo apt-get update", and post the output so we can see what it's *trying* to do.

Lloyd B.

---

### Post by thoriumchameleon on 2009-09-29
do you have gcc installed? if not it may cause this to happen.. if you're new to linux you should use synaptic package manager... its a lot more user friendly than a terminal!

EDIT: it looks like you can at least attempt to compile... what are you using to compile?

---

### Post by xvkkd on 2009-09-29
Thanks lloyd_b..

I have typed in "sudo apt-get update" and this is what I have got.

"Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg                   
Ign [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) feisty Release.gpg                          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_HK        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_HK  
Ign [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) feisty/main Translation-en_HK             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_HK  
Ign [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) feisty/restricted Translation-en_HK
Ign [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) feisty/universe Translation-en_HK
Ign [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) feisty/multiverse Translation-en_HK
Ign [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) feisty/multiverse Translation-en_HK
Ign [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) feisty/universe Translation-en_HK
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_HK
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_HK
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_HK
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Ign [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) feisty-updates Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Ign [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) feisty-updates/main Translation-en_HK
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Ign [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) feisty-updates/restricted Translation-en_HK
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Ign [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) feisty-updates/multiverse Translation-en_HK
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Ign [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) feisty-updates/universe Translation-en_HK
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
  404 Not Found
Ign [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) feisty Release
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
  404 Not Found
Ign [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) feisty-updates Release
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
  404 Not Found
Ign [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) feisty/main Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
  404 Not Found
Ign [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) feisty/restricted Packages
Ign [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) feisty/main Sources
Ign [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) feisty/restricted Sources
Ign [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) feisty/universe Packages
Ign [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) feisty/universe Sources
Ign [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) feisty/multiverse Packages
Ign [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) feisty/multiverse Sources
Ign [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) feisty/multiverse Packages
Ign [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) feisty/universe Packages
Ign [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) feisty-updates/main Packages
Ign [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) feisty-updates/restricted Packages
Ign [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) feisty-updates/main Sources
Ign [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) feisty-updates/restricted Sources
Ign [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) feisty-updates/multiverse Packages
Ign [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) feisty-updates/universe Packages
Err [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) feisty/main Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) feisty/restricted Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) feisty/main Sources
  404 Not Found [IP: 91.189.88.46 80]
Err [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) feisty/restricted Sources
  404 Not Found [IP: 91.189.88.46 80]
Err [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) feisty/universe Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) feisty/universe Sources
  404 Not Found [IP: 91.189.88.46 80]
Err [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) feisty/multiverse Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) feisty/multiverse Sources
  404 Not Found [IP: 91.189.88.46 80]
Err [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) feisty/multiverse Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) feisty/universe Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) feisty-updates/main Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) feisty-updates/restricted Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) feisty-updates/main Sources
  404 Not Found [IP: 91.189.88.46 80]
Err [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) feisty-updates/restricted Sources
  404 Not Found [IP: 91.189.88.46 80]
Err [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) feisty-updates/multiverse Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) feisty-updates/universe Packages
  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://hk.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://hk.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://hk.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz](http://hk.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://hk.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz](http://hk.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://hk.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz](http://hk.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://hk.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://hk.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://hk.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz](http://hk.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://hk.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz](http://hk.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://hk.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz](http://hk.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://hk.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz](http://hk.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://hk.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://hk.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://hk.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz](http://hk.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://hk.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz](http://hk.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://hk.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz](http://hk.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://hk.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz](http://hk.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://hk.archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/binary-i386/Packages.gz](http://hk.archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://hk.archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/binary-i386/Packages.gz](http://hk.archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead."

There is quite a lot of material. Sorry if it seems messy. BTW, I am also using the Ubuntu 7.04. Thanks.

---

### Post by xvkkd on 2009-09-29
.

---

### Post by Johnny B on 2009-09-29
feisty is not supported anymore, that may be your problem.
run sudo aptitude dist-upgrade

---

### Post by xvkkd on 2009-09-30
Hi Johnny B,

Thanks for the tip. I have typed in "sudo aptitude dist-upgrade" and this is what I got:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

Nothing seemed to have changed.

---

### Post by lloyd_b on 2009-09-30
Feisty is a pretty old version (07.04, so about 2 1/2 years old), and is not an LTS (long term support) release, so there may not be an easy way to upgrade.

You can *try* the following, BUT IT MAY TOTALLY MESS UP YOUR SYSTEM.  That said, edit the file "/etc/apt/sources.list", and change every instance of "feisty" to "hardy".  Note that this is a root owned file, so you'll need "sudo nano /etc/apt/sources.list" to be able to edit it.

Then, run "sudo apt-get update", and then "sudo apt-get dist-upgrade".  If this works correctly, it'll bring your system up to version 08.04, which *is* an LTS release and will have working repositories for at least another 1 1/2 years.

Personally, I would just download the latest install CD image, and install from scratch with the latest version.  It's your choice which way to go, but you are not going to be able to get a working build system until you get the system updated to something more recent.

Lloyd B.

---

### Post by Johnny B on 2009-09-30
xvkkd:  I'm only assuming that you are running feisty
please run > lsb_release -a and make sure it says feisty

---

### Post by xvkkd on 2009-10-02
Hi Johnny B,

When I typed  lsb_release -a, this is what I got

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 7.04
Release:        7.04
Codename:       feisty

---

### Post by lloyd_b on 2009-10-03
> **xvkkd said:**
> Hi Johnny B,

When I typed  lsb_release -a, this is what I got

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 7.04
Release:        7.04
Codename:       feisty

Yep - you're running Feisty.

Question: Do you still have the CD that you installed from?  If so, you can use the "apt-cdrom" command to add the packages on that CD to the list of available packages.  Just type "sudo apt-cdrom" in a terminal window, and when prompted put the CD in the drive (assuming everything is configured correctly, this should be all there is to it).

Once you've added the CD, try "sudo apt-get build-essential" again, and it should fetch the packages from the CD rather than from the network.

Lloyd B.

---

### Post by MaxIBoy on 2009-10-03
> **lloyd_b said:**
> Feisty is a pretty old version (07.04, so about 2 1/2 years old), and is not an LTS (long term support) release, so there may not be an easy way to upgrade.

You can *try* the following, BUT IT MAY TOTALLY MESS UP YOUR SYSTEM.  That said, edit the file "/etc/apt/sources.list", and change every instance of "feisty" to "hardy".  Note that this is a root owned file, so you'll need "sudo nano /etc/apt/sources.list" to be able to edit it.

Then, run "sudo apt-get update", and then "sudo apt-get dist-upgrade".  If this works correctly, it'll bring your system up to version 08.04, which *is* an LTS release and will have working repositories for at least another 1 1/2 years.

Personally, I would just download the latest install CD image, and install from scratch with the latest version.  It's your choice which way to go, but you are not going to be able to get a working build system until you get the system updated to something more recent.

Lloyd B.
NO! DON'T DO IT THAT WAY!!!! It is very important that you should update one version at a time, leaping many versions is not supported and WILL NOT WORK!

You need to go to your /etc/apt/sources.list. (Edit it with sudo.)

Change all references of "http://archive.ubuntu.com/ubuntu/" into "http://old-releases.ubuntu.com/ubuntu" instead. Now you will be able to install packages from the repositories or upgrade distros!



Now, you can do one last 
```
sudo apt-get update
sudo apt-get upgrade
``` You will never need to do this again because feisty isn't being updated anymore. If you like you can stick with feisty forever, adding whatever (obsolete) packages are in its repos. But I highly recommend, both because of new features, and because of security fixes, that you continue to upgrade. 

Now edit the sources.list again file and changing all references of "feisty" to "gutsy". Now do ```
sudo apt-get update
sudo apt-get dist-upgrade
```Finally, you can revert "http://old-releases.ubuntu.com/ubuntu" to "http://archive.ubuntu.com/ubuntu/", because now we are about to upgrade to Ubuntu 8.04, and this is no longer in the "old-releases" repository. You now change all references of "gusty" to "hardy"--```
sudo apt-get update
sudo apt-get dist-upgrade
```
Finally, you are now running a version which is currently supported. If you like you can contintue to update to the latest and greatest, or you can stick with Ubuntu 8.04. Ubuntu 8.04 will be supported until I believe 2011.

---

