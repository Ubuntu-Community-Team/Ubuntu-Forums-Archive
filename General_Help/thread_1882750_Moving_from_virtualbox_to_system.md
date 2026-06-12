---
title: "Moving from virtualbox to system?"
date: 2011-11-17
forum: General Help
---

### Post by pepsifx357 on 2011-11-17
Ok, treat me like a newbie on this one, because I have no idea where to start.

Say I get a system up and running in virtualbox.  This system is exactly the way I want it.

How would I migrate from virtualbox to a real system?

1. What would be the proper way to backup the entire virtual system?
2. Would I boot into a live CD to implement the install?
3. How would I format the bare boned hard drive?
4. How would I then inject the system onto the hard drive?
5. How would I get it to boot and work correctly?

I'm assuming a normal full system backup using tar and omiting "/dev/*" "/mnt/*" would take care of number 1.  I'm also assuming that number 2 is correct.  The rest I have no clue.

Thanks,

Ben

---

### Post by jjex22 on 2011-11-17
heya, 

Firstly I suppose the 'proper' way to back up would be like [this]("http://www.ehow.co.uk/how_8551106_back-up-virtualbox.html")

But I don't really bother with that, because it's just too much work - at the end of the day your virtual hard drive will just be a .vdi file on your operating system, so I just back it up with my weekly backup.

I'll do as requested and give a noob's intro to virtualbox, hope I don't cause any offence!

obviously first things first is download it! you can get it straight from apt-get or go to the virtualbox site and download a package for your ubuntu version - advantage of this is it'll be current, so you won't immediately be told to upgrade - last i checked the repo version wasn't the newest - may have changed!

Anyway once you've downloaded and started virtualbox, you need an installation cd/iso/img file of the os you want to install be it unix/windows (osx is only supported on osx).

first you create the new virtual hard drive - this will just be a file in ubuntu (which will now become your host OS) - you click create new virtual hard drive , then a wizard opens and you tell it what OS you want to install and where the cd/iso is.

The rest of the wizard will create the virtual hard drive, but it's really creating a virtual computer as well - it'll ask you how big you want the HDD for the guest to be and how much ram you want to give it -these are sacrificed from your host os - so if you have say 3gb ram, don't set the virtual machine's ram at say 2.5 or you'll only leave ubuntu half a gig! - but it's very informative and easy to do.

 
once it's set up, you just install the os into it,(making this the guest os) exactly like installing on a real pc. as soon as it's installed you click on device - install virtualbox tools - basically the drivers for the machine so it runs faster and networks to the host!

The network is the most important part - no only is this how the guest os connects to the internet from inside virtualbox, it's also how you share files between the two systems - even though it's running in a windo on your desktop, using your resources they are for all intents and purposes completely separate machines and virtualbox tools creats a network between them.

a couple of tips

1) pre windows 2000 sp4 versions of microsoft are not supported by the tools, and whilst I have got dos onwards working, you wither have to manually set up a network between guest and host or copy files via usb/cd

2) it's so easy to do you'll probably end up with several virtual machines on your hdd, taking up quite a bit of room - so i find it's best to put them on a seperate partition/hdd - also makes backing them up easier to manager if like my you just back them up as part of a general back up.

3)if you have a laptop and a desktop and you use virtualbox/vmware on both you can transfer your virtual hdds by usb key to use on both systems.


hope that helps!

---

### Post by jjex22 on 2011-11-17
To get an idea what I mean, probably worth checking out you tube - people seem to have made a virtual box installation guide for almost every os!

---

### Post by drmrgd on 2011-11-18
I think you may have misunderstood the question.  The OP was asking how to migrate his Virtual Box OS to a live system, not how to set up an OS in Virtual Box.  I am also wondering how one might go about this.  From a quick cursory Google search, seems like a lot of people want to do the opposite (i.e. move a live OS to Virtual Box).

---

### Post by BillyBoa on 2011-11-18
> **pepsifx357 said:**
> Ok, treat me like a newbie on this one, because I have no idea where to start.

Say I get a system up and running in virtualbox.  This system is exactly the way I want it.

How would I migrate from virtualbox to a real system?

1. What would be the proper way to backup the entire virtual system?
2. Would I boot into a live CD to implement the install?
3. How would I format the bare boned hard drive?
4. How would I then inject the system onto the hard drive?
5. How would I get it to boot and work correctly?

I'm assuming a normal full system backup using tar and omiting "/dev/*" "/mnt/*" would take care of number 1.  I'm also assuming that number 2 is correct.  The rest I have no clue.

Thanks,

Ben

I think the answer is Remastersys.

You can create an ISO file using the filesystem on which it’s being run. You will clone your system. You can create the ISO and then you pass it to a CD.

---

### Post by haqking on 2011-11-18
remastersys or clonezilla.

However remember that in a VM it is virtualised hardware and may not necessarily run as well on the real hardware, make sure you know the hardware works.

There may be some configurational changes needed to be made.

But other than that, clone the VM and clone it back to the destination (destination needs to be same size or larger than source)

Cheers

---

### Post by blueridgedog on 2011-11-18
From withing the guest os:

1.  Remastersys is no longer being developed, use the fork [http://re-linux.sourceforge.net/](http://re-linux.sourceforge.net/)
or
2.  Simply make a backup of your entire home directory then make a backup of your installed packages: [http://www.ubuntu-unleashed.com/2008/04/howto-restore-all-installed-packages-in.html](http://www.ubuntu-unleashed.com/2008/04/howto-restore-all-installed-packages-in.html)

---

### Post by haqking on 2011-11-18
> **blueridgedog said:**
> From withing the guest os:

1.  Remastersys is no longer being developed, use the fork [http://re-linux.sourceforge.net/](http://re-linux.sourceforge.net/)
or
2.  Simply make a backup of your entire home directory then make a backup of your installed packages: [http://www.ubuntu-unleashed.com/2008/04/howto-restore-all-installed-packages-in.html](http://www.ubuntu-unleashed.com/2008/04/howto-restore-all-installed-packages-in.html)

1. Remastersys is being developed again, he started again about month ago i believe.

Fragadelic has a thread on here about it [http://ubuntuforums.org/showthread.php?t=1870607](http://ubuntuforums.org/showthread.php?t=1870607)

---

### Post by BillyBoa on 2011-11-18
To install Remastersys

```
sudo gedit etc/apt/sources.list
```

add 

[HTML]deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic/ [/HTML]

```
sudo apt-get update && sudo apt-get install remastersys
```

---

### Post by blueridgedog on 2011-11-18
> **haqking said:**
> 1. Remastersys is being developed again

Ah...good news then.  I liked the tool.

---

### Post by pepsifx357 on 2011-11-19
so it looks like remastersys is the answer.

Thanks guys!

---

