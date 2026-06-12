---
title: "How to avoid this? Windows writing to Ubuntu drive!"
date: 2010-07-09
forum: General Help
---

### Post by ve2 on 2010-07-09
I have 2 hard drives. One with Windows XP and the 2nd with Ubuntu 10.04. All is good on the install and the boot up for both. But untill I start installing software like Ms Office 2003 it buggers up the boot and I had found that MS Office is writing temp files to the Ubuntu drive. Thus the systems stops!! I mean no more OS on both drives booting... Any ideas?

---

### Post by efflandt on 2010-07-10
What does **sudo fdisk -l** show for your partitions and what filesystems are on them?  WinXP should certainly not natively try to write to common Linux filesystems.

I dual boot WinXP (or Win7) on several computers, and nothing in Windows has written to the Linux partitions.

---

### Post by ve2 on 2010-07-10
Ok you are so right! Its even a better! I tested this by installing 3 software programs...and finally i found that the 3rd one.. Adobe Photoshop 2 effected the boot. No idea why... boot will not come up.. period..???? It just keeps re-booting...????

---

### Post by WorMzy on 2010-07-10
I think the problem is most likely either a) a failing harddisk or B) a lose cable. Installing a program should not, in any way, make changes to the MBR, regardless of whether you're using Windows or Linux or any other form of operating system.

---

### Post by Seeked on 2010-07-10
When you boot into windows... before the MBR is messed up, go into your device manager right click on the drive you don't want windows working with and disable it. It will still work for Linux.

---

### Post by ve2 on 2010-07-10
Ok - so the boot manager is not coming up. Can't get into windows or ubuntu. Now as per the idea of a failing harddrive or cable.. This only happens when I install Adobe Photoshop CS2 when Ubuntu is on drive d:
 
I am now re-installing Ubuntu on Drive d: to see if I can boot up. I also tried to re-install grub via the terminal per previous posts - all fails and gives me errors... moving along. (I know may I could be more patient - but I need the machine today...I could simply put this to the side and tackle it another day)
 
But I need to know in the event of boot failure, what can I do? Is there a Ubuntu Rescue disk I can create??
 
In this test case I have not installed any software in Ubuntu as I typical would like to. If all fails.. I will have to just disconnect the power cable to either one of the drives before installing windows software. 
 
Ok Ubuntu has finished installing. I'm now rebooting the machine.
 
(I know long process to make such a test...but Ubuntu installs fairly quickly)
 
WOW!! The boot manger is back???? Why is that?? The machine is back to where it was prior... And all is good.. Ubuntu loads properly... and Now checking windows...Looking for Photoshop CS2 - and yes there it is... loading it, works fine. Started all 3 programs that were installed..and all work. Now rebooting and the boot manager is still working. Good!!!
 
Ok - so what's the cause of this? Photoshop CS2 doing some nasty stuff to the boot?? OMG how on earth??? OK... so i'm going to reinstall the adobe program CS2...But 1st I will remove it 1st to see if this has effect, nothing... back in windows now. Installing CS2, rebooting and back to no boot screen, wow!!! why???
 
:(

---

### Post by mike555 on 2010-07-10
I thought that if you installed Ubuntu using ext4 file system , that Windows could not write to it even if you wanted to ..


 of course the MBR probably isn't ext4 though..

---

### Post by ve2 on 2010-07-10
I did this in ext3 - no idea how to change or protect the MBR.

---

### Post by yetiman64 on 2010-07-10
What is the brand / specs (including model number) of your machine. 

Have heard of MBR being written to with some HP and Dell machines. But otherwise this sounds weird that an app like adobe PS could be doing this.

---

### Post by ve2 on 2010-07-10
Home built machine P5QL Pro board, 4GB ram, 3 hard drives total is 4TB - 1GB Video card, And Quad processor. I will have to look at another concept.

---

### Post by ve2 on 2010-07-10
If i install Ubuntu alone - without placing the boot on the hda - where on hdb would i place it?

---

### Post by yetiman64 on 2010-07-10
With a home built machine like that reconsider what WorMzy said in post #4 about checking harddrives/cables etc. 

Maybe go to the HDD manufacturers site and see if there are any downloadable drive diagnostics programs etc if the cabling is all OK.

Very weird situation that really shouldn't be happening and would have me suspecting my hardware if it happened here.

---

### Post by ve2 on 2010-07-10
txs :)

---

### Post by oldfred on 2010-07-10
Beside the HP & Dell machines having applications that write into the MBR there have been a few other applications that hide serial numbers or settings in the MBR.

Since you have two drives, put the window boot loader back on the MBR or the drive with windows and install grub to the other drive's MBR. Then set the BIOS to boot the Ubuntu drive.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by dino99 on 2010-07-10
are you sure about windows security files: check for virus, sniffer, trojan and other worms etc

---

### Post by mike555 on 2010-07-10
You might want to do what I do, install grub to the same partition as Ubuntu (because Ubuntu needs it to boot) and use a different boot loader like " Gag " , in the MBR ... 
[http://gag.sourceforge.net/](http://gag.sourceforge.net/)

---

### Post by ve2 on 2010-07-10
Gag I like!!! Yes any BOOT MANAGER would be better than the one I have (no offense) - But how about the 3 drive I have as the back-up drive. It has a MBR - can I not install it there? But Gag seems easy enough!

---

### Post by ve2 on 2010-07-10
Ok so installed the boot loader on the Ubuntu hard drive. Windows sitting on it own drive and installed CS2 and I have no issues...
 
Mind you I have to boot via the BIOS boot selector via F8, not a big deal. I have downloaded GAG, it's asking for a diskette, ummmm.. I don't have that on my machine. I guess I could get one, but is there another method for the GAG program.
 
Overall - all is good now..
 
Ubuntu has it owns real estate of 1TB (i doubt I will ever fill that)
Windows also sitting alone on 1TB - that I know I will fill with the video work I do.
And my 2TB back-up is safe and sound sitting alone.
 
Now if I could get a 3rd party FREEWARE type boot manager - I'd be pretty happy!

---

### Post by ve2 on 2010-07-10
> **dino99 said:**
> are you sure about windows security files: check for virus, sniffer, trojan and other worms etc
 
Did virus scan on MBR using Avast "whatever that's worth" and was reported virus free.:popcorn:

---

### Post by COKEDUDE on 2010-07-10
> **mike555 said:**
> You might want to do what I do, install grub to the same partition as Ubuntu (because Ubuntu needs it to boot) and use a different boot loader like " Gag " , in the MBR ... 
[http://gag.sourceforge.net/](http://gag.sourceforge.net/)

Would having grub and gag conflict with each other?

---

### Post by ve2 on 2010-07-10
I doubt it of the boot for Ubuntu is installed on its own drive. I personally can live with F8 and boot from my machines boot selector... Many thanks to all!! Awesome banter of ideas.:D

---

### Post by oldfred on 2010-07-10
If you run this grub should find the window and let you boot it. Of course with the windows boot loader in sda you still can boot it with the BIOS. One real advantage of  multiple drives.
```
sudo update-grub
```

---

### Post by ve2 on 2010-07-11
Seems much easier for me when they all have thier own drives. Thank you all!!:)
 
Overall UBUNTU had nothing to do with the original topic... It was a WINDOWS deal...
 
I was looking at installing several distro's of Linux, but it seems much easier in Virtualbox... Better than messing around with the hard drive.

---

