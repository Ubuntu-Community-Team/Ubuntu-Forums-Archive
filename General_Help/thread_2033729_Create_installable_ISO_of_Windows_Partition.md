---
title: "Create installable ISO of Windows Partition"
date: 2012-07-26
forum: General Help
---

### Post by AlistairH on 2012-07-26
My PC is currently configured to dual boot, which I rarely do. The only time I need to go into Win 7 is on the odd occasion I need to refer to something when supporting a remote user on the phone.

I'd like to convert my machine to a dedicated Linux box and have Win 7 run in a VirtualBox on the rare occasion I need it.

Since I bought this machine on eBay, I don't have the original install disk so I'd like to create an installable ISO from the Win 7 partition and use that to install Win 7 into VirtualBox.

Is this at all possible?

If so, I'll take the opportunity of upgrading Ubuntu from my current version of 10.04.

---

### Post by Primefalcon on 2012-07-26
you could clone it to the vm.... the thing with windows though, it gets very hardware dependent and if it detects too much change in hardware, it'll lock down and require you to cal Microsoft to explain yourself...

Clonezilla as far as I know should be able to do this...

---

### Post by QIII on 2012-07-26
Make your Windows recovery disk so you can reinstall on the machine if need be.  If you deleted your Recovery partition, that rules that out. Recovery disks, however, cannot be used to install in VMs.

You might be able to use Conezilla to clone to another disk if you have the hardware to do that.  But that would only work if that disk was subsequently used on the same machine.  Typically, OEM installs are specific to a single motherboard.  You might then be able to just swap out disks when you wanted to.  No guarantees, of course.

There are legal problems in creating a bootable "install" disk the way you suggest, so don't go googling.

And my dog is way cooler than Primefalcon's.

---

### Post by Mark Phelps on 2012-07-27
While you could make a backup of your Win7 installation -- that will NOT produce a re-installable copy.  That copy can only be RESTORED to a partition -- a very different function than reinstallation.

The link below confirms this:

[http://askubuntu.com/questions/13390/moving-windows-7-to-a-virtual-machine]("http://askubuntu.com/questions/13390/moving-windows-7-to-a-virtual-machine")

---

### Post by vexorian on 2012-07-27
> **AlistairH said:**
> My PC is currently configured to dual boot, which I rarely do. The only time I need to go into Win 7 is on the odd occasion I need to refer to something when supporting a remote user on the phone.

I'd like to convert my machine to a dedicated Linux box and have Win 7 run in a VirtualBox on the rare occasion I need it.

Since I bought this machine on eBay, I don't have the original install disk so I'd like to create an installable ISO from the Win 7 partition and use that to install Win 7 into VirtualBox.

Is this at all possible?

If so, I'll take the opportunity of upgrading Ubuntu from my current version of 10.04.
What you can do is use Clonezilla: [http://clonezilla.org/](http://clonezilla.org/)  Since windows 7 partitions are ultra large, it is better you get a portable hard drive. Portable hard drives are very useful for backups and stuff, and you will not regret this purchase if you can do it. CDs/DVDs are prone to scratches.


Make a CloneZilla live CD, or install it on the portable hard drive (If you do this, in a different partition).

From the CloneZilla live CD, you can copy win7's partition to the external hard drive.

Edit: Oh, since you just want to move it to VirtualBox, then you can save the image of the partition in your Ubuntu partition using CloneZilla.

Then you return to ubuntu and you can boot CloneZilla's CDs on the virtual box computer.

However, there is good (VERY good) chance that your windows 7 installation will not boot when put on virtual Box.

Windows has this thing that makes it fail whenever you switch motherboard and CPU. I had difficulties even moving windows XP from my old virtual box from years ago to a new one. (VirtualBox emulates a whole machine, so it is like it will have a different motherboard and CPU).

You *might* have a chance to make it work if you first disable all your motherboard/processor specific drivers before making the CloneZilla image.

Edit: [Here are instructions](http://www.pcworld.com/article/200827/upgrade_your_motherboard_the_easy_way.html) about how to move a win7 hard drive from a computer to another without having to do a clean install. Follow them, and just remember that virtual box is the new computer (new motherboard), etc).

Provided you have enough space in the ubuntu partition, you should not have to remove your windows 7 partition until you successfully boot it in virtualBox (**If** it is possible, I am not sure it will work, because even if you get to move it correctly, there might be protections that stop the OS working on a machine different to the one the OEM is meant to...).

---

