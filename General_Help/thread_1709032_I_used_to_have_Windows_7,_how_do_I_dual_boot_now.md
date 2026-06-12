---
title: "I used to have Windows 7, how do I dual boot now?"
date: 2011-03-17
forum: General Help
---

### Post by kheaven on 2011-03-17
I used to have Windows 7 as my OS, but now I just have ubuntu.
Is there a way for me now to dual boot Windows 7 and ubuntu?

---

### Post by TimEnid on 2011-03-17
follow the directions here
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by Muster Mark on 2011-03-17
Do you need to run it as a duel boot?  It would probably be a lot simpler to run Win7 in VirtualBox or the like, unless you plan on using very hardware intensive software in Win7.  Actually, if you just need to use some software, you should check to see how well it works with WINE.

That said it shouldn't be too hard to do what you are asking. I have only gone the other way (installed Ubuntu to duel boot on a Win7 machine), so I don't really know how what you are asking is done.  I would guess that it's as simple as creating a NTFS formatted partition on your drive with GParted or the like, installing Win7 on that, and then messing with GRUB so that you can boot from it, although there could definitely be something I am not thinking of.

Cheers and Good Luck!

---

### Post by TimEnid on 2011-03-17
Like Muster said, i prefer running it in a virtual box as well. There might come a time when you feel you dont need it anymore. Its less of a process to remove it from a virtual box.

---

### Post by wilee-nilee on 2011-03-17
If you would like specific instructions, post a screen shot of gparted. To install gparted it in Ubuntu run in the terminal
sudo apt-get install gparted

To use gparted to repartition though a live cd will be used, you can't resize the partition you are running on.

Windows 7 is a bit tricky if you don't make a partition for it marked with a boot flag it will create two partitions, a boot partition and the main OS **this** will unallocate any adjacent partition. You can build as many that will fit and keep within the amount of primary type partitions otherwise.

---

### Post by kheaven on 2011-03-17
> **Muster Mark said:**
> Do you need to run it as a duel boot?  It would probably be a lot simpler to run Win7 in VirtualBox or the like, unless you plan on using very hardware intensive software in Win7.  Actually, if you just need to use some software, you should check to see how well it works with WINE.

That said it shouldn't be too hard to do what you are asking. I have only gone the other way (installed Ubuntu to duel boot on a Win7 machine), so I don't really know how what you are asking is done.  I would guess that it's as simple as creating a NTFS formatted partition on your drive with GParted or the like, installing Win7 on that, and then messing with GRUB so that you can boot from it, although there could definitely be something I am not thinking of.

Cheers and Good Luck!

I am complete new to using ubuntu and I'm not sure what virtual box is.

---

### Post by Muster Mark on 2011-03-18
Hey, no worries.

VirtualBox is an application that enables you to run what are called "virtual machines".  I'm not a computer scientist, but my understanding of this is that the virtual machine software (virtualbox in our case) creates what seems like a hardware interface (at least to an operating system) in software.  Thus, you can run an operating system on this "hardware" that is actually being made by the virtual machine software.  So, when the operating system you run on a virtual machine thinks it's interacting with the hardware (allocating memory for various tasks, accessing the disk etc.) it is actually giving these commends to virtualBox, which makes resource requests like any other application.

Fortunately you don't need to know any of this stuff to use VirtualBox (heck, I may even be wrong about it).  The important thing is that software like VirtualBox lets you run operating systems like you would any other application, within whatever operating system you are running VirtualBox.  This has many advantages, since you don't have to repartition your drive, and you can use Win7 while running Ubuntu.  The only disadvantage is that your computer resources are split between running two operating systems simultaneously (i.e. this will take a good amount of RAM), but that shouldn't be too much a problem unless you plan on doing something like video editing or some such while running the virtual machine (or unless you don't have much RAM.  I would say 4GB or even 3GB should be just fine, although I have never run Win7 and Ubuntu together, so I don't know first hand.  2GB is pushing it since that is the minimum system requirement for 64bit windows (you only need 1 GB though for 32 bit)).

Anyway, the first step is to install VirtualBox: [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads) Double clicking the .deb file that you download will open the Ubuntu software center, which gives you the option to install it (which takes a little time).  After that, just go to Applications->System Tools->Oracle VM VirtualBox.  It will then give you instructions for setting up the virtual machine (which is pretty easy, IIRC).  Let us know how it goes.

Cheers and good luck!

---

### Post by kheaven on 2011-03-18
> **Muster Mark said:**
> Hey, no worries.

VirtualBox is an application that enables you to run what are called "virtual machines".  I'm not a computer scientist, but my understanding of this is that the virtual machine software (virtualbox in our case) creates what seems like a hardware interface (at least to an operating system) in software.  Thus, you can run an operating system on this "hardware" that is actually being made by the virtual machine software.  So, when the operating system you run on a virtual machine thinks it's interacting with the hardware (allocating memory for various tasks, accessing the disk etc.) it is actually giving these commends to virtualBox, which makes resource requests like any other application.

Fortunately you don't need to know any of this stuff to use VirtualBox (heck, I may even be wrong about it).  The important thing is that software like VirtualBox lets you run operating systems like you would any other application, within whatever operating system you are running VirtualBox.  This has many advantages, since you don't have to repartition your drive, and you can use Win7 while running Ubuntu.  The only disadvantage is that your computer resources are split between running two operating systems simultaneously (i.e. this will take a good amount of RAM), but that shouldn't be too much a problem unless you plan on doing something like video editing or some such while running the virtual machine (or unless you don't have much RAM.  I would say 4GB or even 3GB should be just fine, although I have never run Win7 and Ubuntu together, so I don't know first hand.  2GB is pushing it since that is the minimum system requirement for 64bit windows (you only need 1 GB though for 32 bit)).

Anyway, the first step is to install VirtualBox: [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads) Double clicking the .deb file that you download will open the Ubuntu software center, which gives you the option to install it (which takes a little time).  After that, just go to Applications->System Tools->Oracle VM VirtualBox.  It will then give you instructions for setting up the virtual machine (which is pretty easy, IIRC).  Let us know how it goes.

Cheers and good luck!

My computer actually says that I only have 4gb of ram.
Would it be better to dual boot it without the use of virtual box?
If so, how.
Thanks again.

I have installed VirtualBox and I have gone through the settings, but when I choose to start the machine it says:
"FATAL: No bootable medium found! System halted."

Update: I think the problem is that I don't have an ISO of Windows 7.
I am currently downloading the 64bit one from this torrent.


Can anyone verify that what I am doing is correct?
If so, what do I do next?

---

### Post by Muster Mark on 2011-03-18
You need to install the OS you want to run onto the virtual hard disk that VirtualBox helped you make in the setup wizard.  Normally, if you have an install DVD in the computer, the first time you boot up the VM it boots from that, since it doesn't have an OS on the virtual hard drive.  However, you only have an .iso so you need to tell it that you will be using a virtual install DVD.

BTW, I have no idea if the sight you linked to is legit or what or if the .iso you would download from them is even a bootable installer, or if it is just the service pack.  I hope it is.

Right click on your virtual machine (from the Virtual Box main window) and click "settings" and go to the "storage" section.  go to the CD/DVD (this might be called 'IDE secondary master (CD/DVD)').  Click on the CD icon that under the "IDE Controller".  On the right of the settings window there should be a drop down list for choosing CD/DVD drive.  next to the list is an icon of a CD.  Click it to choose a virtual CD/DVD (and choose your .iso file).  Then just start you virtual machine!  You might get a whole bunch of popup warnings about key capture etc. These aren't bad.  That's all I can think of right now, hope that's all the info you need.  Keep us posted.

Cheers,

---

### Post by bumder on 2011-03-18
if you look on youtube, i'm sure there are many guides on how to do what you are looking for.

essentially you do want an iso file, which is a disc image that can be mounted on virtualbox/linux. in fact, you would have to do this if you had a netbook that had no cd/dvd drive for example.

i would remove that link if i were you, and don't mention torrents on here (mods won't like it).

---

### Post by kheaven on 2011-03-19
> **Muster Mark said:**
> You need to install the OS you want to run onto the virtual hard disk that VirtualBox helped you make in the setup wizard.  Normally, if you have an install DVD in the computer, the first time you boot up the VM it boots from that, since it doesn't have an OS on the virtual hard drive.  However, you only have an .iso so you need to tell it that you will be using a virtual install DVD.

BTW, I have no idea if the sight you linked to is legit or what or if the .iso you would download from them is even a bootable installer, or if it is just the service pack.  I hope it is.

Right click on your virtual machine (from the Virtual Box main window) and click "settings" and go to the "storage" section.  go to the CD/DVD (this might be called 'IDE secondary master (CD/DVD)').  Click on the CD icon that under the "IDE Controller".  On the right of the settings window there should be a drop down list for choosing CD/DVD drive.  next to the list is an icon of a CD.  Click it to choose a virtual CD/DVD (and choose your .iso file).  Then just start you virtual machine!  You might get a whole bunch of popup warnings about key capture etc. These aren't bad.  That's all I can think of right now, hope that's all the info you need.  Keep us posted.

Cheers,

It worked.
Thank you so much.

---

