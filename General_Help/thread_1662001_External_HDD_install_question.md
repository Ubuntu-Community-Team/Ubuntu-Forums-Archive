---
title: "External HDD install question"
date: 2011-01-07
forum: General Help
---

### Post by iTwoFour on 2011-01-07
Hi all. I'm new to the site (and Ubuntu) and I need some help or at least some advice on installing Ubuntu to my HDD. I know this has been addressed quite a few times here but I couldn't find any information on my particular predicament. Also, I wouldn't call myself a 'newb' to computers but am no expert so bear with me :) 

So, I just reformatted an old computer of mine and I plan to dual boot Windows XP and Ubuntu using my external HDD. I have read on how to do this but seeing as I am not sure what to expect I figured I would ask here first before I attempt the install. My main concern is how to go about installing on my external in the first place. I have backup files and a lot of other stuff (pictures, music, etc...) on my external that I don't want to get rid of and I understand that installing Ubuntu directly from GRUB(?) that I will have to erase everything on the HDD. I know that I can partition the external but it will not give me the option to partition it via Disk Management (it is a Seagate FreeAgent Desktop if anyone can help there). Is there any way to install Ubuntu without partitioning the HDD or erasing everything? Or does anyone know how I might be able to partition my external another way? Any advice is greatly appreciated.

---

### Post by McNils on 2011-01-07
I'm sorry but I need to question your choice to install on the external HDD. If you just reformatted the computer why not split the internal disk into a couple of partitions and install on them? Then you can access the external HDD from both windows and ubuntu.

---

### Post by iTwoFour on 2011-01-07
> **McNils said:**
> I'm sorry but I need to question your choice to install on the external HDD. If you just reformatted the computer why not split the internal disk into a couple of partitions and install on them? Then you can access the external HDD from both windows and ubuntu.

I really don't want to for three reasons: 1) I could boot Ubuntu from my laptop if it is on my external, 2) it would save space on my internal HDD, and 3) my particular desktop has three recovery partitions in C: for reformatting and I really don't want to do anything to potentially compromise my ability to reformat if I ever needed to again. However, if I can partition my internal without affecting either recovery partition I wouldn't mind doing that. This is my first time dealing with partitioning and the stuff that goes along with it so I really have no clue as to what I am doing when it comes to that. Pretty much the bottom line is, I don't want to do anything to brick (for lack of a better term) my computer seeing as it is also used occasionally by the rest of my family. Thanks again for any help.

---

### Post by -kg- on 2011-01-08
What kind of laptop is it?  How old is it?  How big is the internal hard drive?  The external?  How much data do you have on each?  The answers to these questions will determine whether you can install on the internal, and whether you can boot to the external.

I recently installed Ubuntu on an old Compaq laptop.  This laptop had XP on it, and only has 10 GB total hard drive space, so a dual boot system is out of the question...it barely had room for XP and I had to constantly clean up the hard drive so it would have sufficient room to operate.

The optical drive is out on the laptop (and is so old I can't buy a replacement), so I had to rely on booting to a flash drive to install.  Unfortunately, the laptop is so old that it doesn't support booting from a USB device.  If yours is similar, an installation to your external would require the Plop boot manager in order to boot to it.

It would be much easier and better to install Ubuntu side-by-side on your internal.  If you install XP on your internal and Ubuntu on your external, and allow GRUB to be installed in the MBR of your computer, the computer will be tied to the external drive...you won't be able to boot either without it connected.

We need the extra information I've asked for.  Helpful would be screenshots of GParted with your partitioning scheme, both of the internal and the external.

Three recovery partitions?  I've never seen a computer with three recovery partitions.  On any laptop I've ever owned, I've only had one.  You don't really need the recovery partitions.  Get in contact with the computer manufacturer and see if you can get an installation disk for it.  If you can, that will eliminate the need for a recovery partition.  All you have to do in that case is make sure and back up any critical data, or use Ghost or some other disk imaging software to create an image of these partitions.

Oh, and for a good tutorial on partitioning operations, read at the link in my signature block.

---

### Post by efflandt on 2011-01-08
Anyone who knows what they are doing, knows that they should **back up** anything they want to keep before tampering with a drive.  And anyone who does NOT know what they are doing should definitely back up anything they do not want to lose.

Linux tools are quite reliable if used properly, but I have seen some situations of people doing things like overlapping partitions, without being able to explain what they did to get into that situation.  So I can only assume they did something incorrectly, because I have never had that happen myself.  Although, I have had to reconstruct partitions with a bit of trial and error when 64-bit WinXP Pro beta totally changed my partition table geometry (cylinders and heads), so it could not boot itself or WinXP Home.

If your external drive has a FAT32 or NTFS partition, you should defrag that first to pack files lower on the drive to make it easier to resize the partition.  Then shrinking a partition can be done relatively quickly with gparted in Linux.  However, if you move the beginning of a partition (or entire partition) that can take a very long time (many hours, or overnight) depending upon its size, because all files are moved relative to the beginning of the relocated partition.

I couple of other issues could crop up even if you properly shrink and create additional partition(s).  The default since Ubuntu 10.04 is to create partitions on MB boundaries instead of cylinder boundaries, but some old PC's cannot cope with that.  A fix is to add the kernel boot parameter **partman/alignment=cylinder** when you boot the live/install CD or iso on USB, or first create the partitions with gparted and check the box in gparted to **align to cylinders** (instead of MB).

Even some new computers have trouble booting farther out on a USB drive, but how far out that is, is still a mystery to me.  For example my new PC has no trouble booting Ubuntu at the far end (beyond 900 GB) of its 1 TB internal drive, but cannot boot Ubuntu at the far end of a 500 GB USB drive (which boots fine on 2 older laptops from 2006).  But the new PC boots fine from the beginning of an identical 500 GB USB drive or anywhere on a 160 GB USB drive.

So even if you do everything right that should work, you may run into a strange situation.  Hence the warning to back up anything you do not want to lose.

PS: One other thing is to make absolutely certain that you install grub to the USB drive and not the default to your internal hard drive, otherwise you may not be able to boot your computer at all without the external drive connected.  In Ubuntu 10.10 that is selected at the bottom of the manual partitioning screen.  Some people recommend unplugging your internal drive while installing to the external drive to avoid having to worry about that.

---

### Post by iTwoFour on 2011-01-08
Well the computer in question is actually a Dell Dimension 3000 installed with Windows XP. It is probably about 5-6 years old and has a 71GB internal with ~63GB of free space on it. The external is 500GB with ~450GB of free space. 

After reading your post and the person before you, it makes more sense to install on the internal. I wouldn't want to be tied down to my external since I use my laptop for school. I was under the impression that I could boot XP when not connected and choose to boot Ubuntu from the boot menu when connected to the external. Even if its possible its probably more work than its worth. 

Here is a screenshot of my partitions as they came on the computer. The top three partitions are my recovery partitions: 

[[IMG]http://img259.imageshack.us/img259/7067/partitionsx.th.png[/IMG]](http://img259.imageshack.us/i/partitionsx.png/)

I have looked into getting a recovery CD but as far as I have found, the only thing you can get close to is a Dell badged version of XP off ebay. Dell stopped making the recovery CD's (or at least stopped distributing them) after they stopped production of the Dimension 3000's. I thought about trying to pull the recovery partitions somehow and save them to my external or some other media but that is way beyond anything I am comfortable with attempting right now.

---

### Post by -kg- on 2011-01-08
Certainly you can install Ubuntu on the external drive, but as efflandt said, you need to make certain that GRUB is installed to the external drive and not to the internal, which is the default.  If you allow GRUB to be installed to the internal drive, the external drive will have to be connected to the computer to boot into anything...even XP.

You also need to make absolutely sure that your machine will boot to a USB device.  You can determine this by going into BIOS and checking whether there is a USB selection in the boot sequence.  It will be there along with Floppy (if you have one), the CD drive, and the hard drive.

If booting to a USB device is not available, all is not lost.  As I said, you can use the [Plop Boot Manager]("http://www.plop.at/en/bootmanager.html") to enable you to boot to a USB device.  I've used it and it works perfectly.

> **efflandt said:**
> PS: One other thing is to make absolutely certain that you install grub to the USB drive and not the default to your internal hard drive, otherwise you may not be able to boot your computer at all without the external drive connected.  In Ubuntu 10.10 that is selected at the bottom of the manual partitioning screen.  Some people recommend unplugging your internal drive while installing to the external drive to avoid having to worry about that.

Have they changed that?  Before (right up to 10.04, which I'm running) the GRUB installation selection was at the very last screen, using the "Advanced" button.

---

### Post by iTwoFour on 2011-01-08
> **-kg- said:**
> You also need to make absolutely sure that your machine will boot to a USB device.  You can determine this by going into BIOS and checking whether there is a USB selection in the boot sequence.  It will be there along with Floppy (if you have one), the CD drive, and the hard drive.

On the boot menu a USB is available to boot from which I assume is my external seeing as I have no other USB's in the computer. I know you can change where GRUB is installed via the Advanced button on the last screen but if it has changed if anyone can let me know I would appreciate it. And one last thing: I'm assuming I should partition my external to avoid losing any of my backup and saved data am I right? And if so how much would you guys recommend setting aside for Ubuntu? Thanks again for all the help.

---

### Post by efflandt on 2011-01-08
In 10.04 or earlier you set where to put grub in the **Advanced** button of the summary screen after you set your username and password.

For 10.10 or later (including Natty) you select where to put grub from the **bottom of the manual partitioning screen**.

I was actually looking for and missed that the first time I installed Maverick to my internal drive, because I intended to put grub on a partition instead of in the mbr.  And sure enough a Dell program stepped on grub2 in the mbr the first time I booted Win7.  But fortunately I also had a bootable USB hd with grub that I could use to boot my internal drive to easily reinstall grub to my primary Linux partition.  Then I restored the standard Windows mbr and marked the partition with grub as the boot partition.

---

