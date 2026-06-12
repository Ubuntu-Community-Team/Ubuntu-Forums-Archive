---
title: "customizing Ubuntu Live CD"
date: 2011-12-12
forum: General Help
---

### Post by Kalebra on 2011-12-12
Hi people I'm new here and also new to Linux. The only experience I've really had with linux is when using my Mac but even thats limited.

So I started work for a company who run a customized version of Ubuntu 10.04 named workbooth. Workbooth has limited access with a lot of features out of date. What I really want to do is unlock locked features such as 'system monitor' and 'terminal' and update some of the software like firefox (currently version 3). Small things like this would just make my job much easier. I'm also wondering if i can install from the live CD directly to my HDD so I have a writable copy to save bookmarks etc and also if I can even update it to ubuntu 11 while still having all features from work.

I have already tried unsquashing it then resquashing it (the file system) using squashfstools on windows via cygwin and I tried it first without modifying but the resquashed filesystem just doesnt seem to work.

Can someone please help me do this I can post the ISO if anyone wants to take a quick look too.

Many thanks in advance

---

### Post by Megaptera on 2011-12-12
If this is a work version, can you ask your work IT dept. for some advice too? Surely they will update the work version?

---

### Post by oldtimer7777 on 2011-12-12
The easiest way to make a customized version of Ubuntu 11.10 is using either Remastersys or Relinux.  Both will create a live.iso file when it is done copying your system, packages, and everything else.  You can migrate that image onto a disc or even better, a live USB Flash Drive with Startup Disc Creator and you can boot from that USB Live custom Ubuntu to do your Custom Ubuntu installations on any computer you want.  

I use it daily. Highly recommended:

[https://debianhelp.wordpress.com/2011/10/12/relinux-a-new-fork-of-remastersys/](https://debianhelp.wordpress.com/2011/10/12/relinux-a-new-fork-of-remastersys/)

Or you can just google for Remastersys and add the repository to install it.

Just install Ubuntu like you normally would on any computer.  Add whatever software you want to it.  Clean it up. Change the wallpaper around if you like, and then with about 5 mouse clicks and about 30-45 minutes you have a live.iso of your entire Ubuntu installed system.  Really nice way to have a rescue disc to reinstall from in case of emergency too. I've used every other method to do this with all the other applications, and I have found remastersys to be the easiest, and most reilable way to make a custom version of current running Ubuntu system.  Everybody should use it.

> **Kalebra said:**
> Hi people I'm new here and also new to Linux. The only experience I've really had with linux is when using my Mac but even thats limited.

So I started work for a company who run a customized version of Ubuntu 10.04 named workbooth. Workbooth has limited access with a lot of features out of date. What I really want to do is unlock locked features such as 'system monitor' and 'terminal' and update some of the software like firefox (currently version 3). Small things like this would just make my job much easier. I'm also wondering if i can install from the live CD directly to my HDD so I have a writable copy to save bookmarks etc and also if I can even update it to ubuntu 11 while still having all features from work.

I have already tried unsquashing it then resquashing it (the file system) using squashfstools on windows via cygwin and I tried it first without modifying but the resquashed filesystem just doesnt seem to work.

Can someone please help me do this I can post the ISO if anyone wants to take a quick look too.

Many thanks in advance

---

### Post by Kalebra on 2011-12-12
Hey unfortunately IT are a bit slow and take a year or 2 to update :-(

I've looked at remastersys before but unfortunately it already runs as a live CD and there's no way to install it. I can't even access basic things like the desktop. I've also tried UCK many times different combos but doesn't seem to work!!

If I sent you the iso could u have a quick look and see what you can do with it? Or tell me any other way around it?

Thanks

---

### Post by Bucky Ball on 2011-12-12
They are using 10.04 LTS for a reason. *Don't* update it. LTS releases are intended for servers and production environments like the one at your work. The desktop has three years support, server version five.

---

### Post by oldtimer7777 on 2011-12-12
So basically, you want to run your own customized version of Ubuntu that you can boot from a USB Flash Drive on your keychain at work.

Again, on your home computer, install Ubuntu, use a walk-through:

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/) 

Follow my above instructions for Remastersys to make a customized version of Ubuntu you need for work, and then migrate that image onto a Live Bootable Flash Drive to boot your work computer from. Startup Disc Creator will help you create the live bootable usb flash drive to use at work, instead of the outdated version you have running on the hdd at work.  Boot from that Flash Drive at work instead now, and you can have what you need without changing the installed Linux system on the work hard drive. That way you won't break any rules at work, you won't get the tech support upset at work for messing around with their computers, and you can have an Ubuntu system to boot from that you can even take home to use later on.

> **Kalebra said:**
> Hey unfortunately IT are a bit slow and take a year or 2 to update :-(

I've looked at remastersys before but unfortunately it already runs as a live CD and there's no way to install it. I can't even access basic things like the desktop. I've also tried UCK many times different combos but doesn't seem to work!!

If I sent you the iso could u have a quick look and see what you can do with it? Or tell me any other way around it?

Thanks

---

### Post by windfix on 2012-01-15
Thank you, for this tip!
(deleted remainder of msg.)

---

### Post by wandalalakers on 2012-01-15
I assume this still holds true.  If using a proprietary driver like Nvidia or ATI, the Remastersys live CD/DVD will not keep that.  So whoever uses the live CD/DVD will have to reinstall that driver.  Basically on a pc in which I used the Nvidia driver from Nvidia.com, I had to reinstall the driver after booting the Remastersys image.  This wasn't hard for me to do but if you gave the live CD/DVD to a client or friend (who has never used linux) who needs the proprietary Nvidia or ATI driver or has the same computer as you do, it would be scary for them to install the driver. (I assume).

---

### Post by sunewbie on 2012-02-08
> **oldtimer7777 said:**
> The easiest way to make a customized version of Ubuntu 11.10 is using either Remastersys or Relinux.  Both will create a live.iso file when it is done copying your system, packages, and everything else.  You can migrate that image onto a disc or even better, a live USB Flash Drive with Startup Disc Creator and you can boot from that USB Live custom Ubuntu to do your Custom Ubuntu installations on any computer you want.  

I use it daily. Highly recommended:

[https://debianhelp.wordpress.com/2011/10/12/relinux-a-new-fork-of-remastersys/](https://debianhelp.wordpress.com/2011/10/12/relinux-a-new-fork-of-remastersys/)

Or you can just google for Remastersys and add the repository to install it.

Just install Ubuntu like you normally would on any computer.  Add whatever software you want to it.  Clean it up. Change the wallpaper around if you like, and then with about 5 mouse clicks and about 30-45 minutes you have a live.iso of your entire Ubuntu installed system.  Really nice way to have a rescue disc to reinstall from in case of emergency too. I've used every other method to do this with all the other applications, and I have found remastersys to be the easiest, and most reilable way to make a custom version of current running Ubuntu system.  Everybody should use it.

Hi,

I am an end user and have limited broadband. I want to ask a basic question. 

I have installed Xubuntu 11.10 and then added lot of apps like xubuntu restricted extras, non-free codecs, Libre Office, some KDE apps like Krita, Okular, K3b etc. and changed panel position

Now, I wish to have a backup with all the deb files of installed software and make a customized xubuntu with all apps installed by default.

The question is, if I select manual mode and then select apps from repos, which I have already installed, does UCK / remastersys re-download it from net? 

Does it need any programming knowledge. I do not want to add my custom themes, or change plymounth themes and artwork like login screen, etc. simply add more apps, so that I can have a full backup LIVE DVD (not data files and folders)

Thanks.

---

### Post by Bucky Ball on 2012-02-08
> **sunewbie said:**
> Hi,

I am an end user and have limited broadband. I want to ask a basic question. 

I have installed Xubuntu 11.10 and then added lot of apps like xubuntu restricted extras, non-free codecs, Libre Office, some KDE apps like Krita, Okular, K3b etc. and changed panel position

Now, I wish to have a backup with all the deb files of installed software and make a customized xubuntu with all apps installed by default.

The question is, if I select manual mode and then select apps from repos, which I have already installed, does UCK / remastersys re-download it from net? 

Does it need any programming knowledge. I do not want to add my custom themes, or change plymounth themes and artwork like login screen, etc. simply add more apps, so that I can have a full backup LIVE DVD (not data files and folders)

Thanks.

Please post a new thread with a descriptive title rather than jumping on this one. You will get more and more specific help. Your problems are really not related to the original OP's and it gets confusing for those trying to help (and those attempting to get help) when dealing with multiple issues on the same thread. ;)

---

### Post by sunewbie on 2012-02-09
ok posted a new thread

[http://ubuntuforums.org/showthread.php?t=1922536](http://ubuntuforums.org/showthread.php?t=1922536)

---

