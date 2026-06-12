---
title: "Problem running Ubuntu 12.04 from external hard drive"
date: 2012-08-19
forum: General Help
---

### Post by tc101 on 2012-08-19
I have two desktop computers, a Dell running ubuntu 10.04, and an Acer running win 7.  I wanted to try out ubuntu 12.04 without messing up anything on the two computers, so to be safe, I decided to install it on an external hard drive.

I plugged a Western Digital My Passport Essential 500 GB USB 3.0/2.0 Portable External Hard Drive into the usb port on the Dell, and to be extra safe I disconnected the internal hard drive.  I put the ubuntu 12.04 CD in the CD drive, turned on the computer and did a fresh install to the external drive.  It worked OK, but when I rebooted I got a message "error:invalid extent. grub rescue".  I repeated the whole process a second time and got the same results.  

Just out of curiosity I plugged the external hard drive into the the Dell, changed the boot order settings, and to my suprise ubuntu 12.04 booted up just fine.

What do you think is going on?  Why won't 12.04 on the external drive run on the Acer (where I did to original install), but runs just fine on the Dell?

One other thing.  I reconnected the win 7 hard drive in the Acer, and using windows explorer I was not able to see the external drive.

---

### Post by darkapec on 2012-08-19
EDIT: reread your post, and u were asking something completely different then I remember reading...

the dell booted cuz the grub on ubuntu 10.04 recognized the 12.04 installation on external drive

the acer did not boot because it is using BCD as the boot manager and it does not by default recognize the ubuntu installation or the EXT4 partition type.

This is also why your windows machine does not read anything on the drive. Windows does not recognize ext2, ext3, or ext4 partitions. 

simple way to test ubuntu out is just boot from the cd and use the LIVE version to see if you like it

---

### Post by tc101 on 2012-08-19
> simple way to test ubuntu out is just boot from the cd and use the LIVE version to see if you like it

I have used it and like it.  I just want to understand how things work.

This is where I am confused

> the dell booted cuz the grub on ubuntu 10.04 recognized the 12.04 installation on external drive


I don't understand this.  I thought the GRUB is stored on the hard drive.  If I change the boot order settings and it hits the external hard drive with 12.04 before the hard drive with 10.04, how does it ever see the grud on 10.04

> the acer did not boot because it is using BCM as the boot manager and it does not by default recognize the ubuntu installation or the EXT4 partition type.


Again I am confused and there must be something I don't understand.  I thought any boot manager was stored on the hard drive, and when I unplugged the internal hard drive with win 7, all the computer will see is what is on the external drive.

---

### Post by NikTh on 2012-08-19
Hi , 
probably this problem occurs cuz external HDD takes little longer to be attached in system rather than internal HDD. 
Thanks

---

### Post by darkapec on 2012-08-19
BCD is the windows boot manager, (I mispoke and said BCM last time).

Grub is stored on the hard drive, but generally when you install ubuntu it will ask you if you want grub installed or to leave the default boot manager, knowing that you can still boot into windows it either did not install grub to the external drive or you pulled the internal drive out during the ubuntu installation and it did not detect windows. 

I say this because in the past when I have done a ubuntu installation on a computer with windows I am always able to boot into ubuntu, but I then have to add windows to grub in order to boot back into windows and your situation seems to be the opposite. 

Also it could just be a USB / grub problem. Ubuntu by default is not really designed to boot from USB and if you use a utility like unetbootin or YUMI you should be able to boot from the USB hard drive without a problem. 

I believe the dell boots because an instance of grub is installed on the internal hard drive (this is assuming you are leaving the internal drive plugged in while you boot from the external) if you are unplugging the internal drive on this machine also, then it is more then likely an instance of the dell using legacy USB that work natively with grub. 

this should be a kinda easy fix, for starters I would do a fresh install and format the external drive to fat32. Then install ubuntu as normal. If during the installation you are prompted to install grub I would select NO. 

The machine will then reboot into windows and then download a tool called EASYBCD this will allow you to add the ubuntu installation on the external drive. 

rebooting the machine again should bring you to a boot menu asking you what you would like to boot to. 

If you decide you do not like ubuntu you can simply unplug the drive, boot into windows run EASYBCD and remove the ubuntu instance. 

I think I have answered your questions let me know if you still have more

---

### Post by tc101 on 2012-08-20
Thanks a lot for all your help.  You said:

> I believe the dell boots because an instance of grub is installed on the internal hard drive (this is assuming you are leaving the internal drive plugged in while you boot from the external) if you are unplugging the internal drive on this machine also, then it is more then likely an instance of the dell using legacy USB that work natively with grub.


I am leaving the hard drive plugged in, but my guess is that is not effecting it, since it reads the external drive first.  My guess is that it might have something to do with that what you said about the dell using legacy USB that works with grub.  The Dell is 3 years older than the ACER.

For now I will leave things as they are while I play with 12.04 on the external drive.  Eventually I will install it on the internal drive.

Thanks again for your help.

---

