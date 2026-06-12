---
title: "MBR's, Hard drives grub, windows"
date: 2012-05-08
forum: General Help
---

### Post by loseby on 2012-05-08
Let me get it correct...... both Windows and Ubuntu will write boot instructions to the MBR.


What happens when you install a windows boot mananger on a hard drive that once had ( or maybe still has ) GRUB on it ?   
Will the PC BIOS recognise both when booting ?  Will one overwrite the other ?

Does Ubuntu install anything on other drives after installation ie. you install it on say a SSD and have a normal sata drive. Does it write any data to that normal sata drive when you connect it ?

---

### Post by jerome1232 on 2012-05-08
When you install Ubuntu it will install part of grub to the boot sector of which ever drive you want it to, by default it will select your first disk. The rest of grub will be placed on Ubuntu's partition under /boot. That's all that will be written.


If you install Windows it will take grub off the boot sector and stick it's boot loader in, if you want to boot Ubuntu again you have to boot from a live cd and reinstall grub to get access to both OS's again.

I hope that answers your question to some extent.

---

### Post by loseby on 2012-05-08
thats a very good start.... thankyou


will the windows boot loader do something similar ie. will that add the choice of boot to windows 7 or Ubuntu or will it totally ignore Ubuntu ( in this case on a totally different drive )


also will GRUB do the same thing ...take windows of the boot sector


And is there a program will will set youi MBR back to stock or would it be best to use the manufacturers tools  ?

And finally, does Ubuntu have a program that can check out a hard drive to see if its faulty ?

---

### Post by jerome1232 on 2012-05-08
Ubuntu's bootloader, grub, can boot many OS's. It will automatically detect your Windows installation and add it as a boot option.

If Windows installs it's bootloader, it will be oblivious to the presence of Ubuntu. This is why it normally recommended to install Windows first, then Ubuntu.

There is no "default" for a boot sector of a drive, You either have a bootloader installed there or you don't. Windows repair cd's come with the utilities to re-install the Windows bootloader and likewise an Ubuntu live cd can be used to reinstall grub.

Ubuntu has SMART disk monitoring (if the disk supports it), which can talk to a drives firmware so that it can warn you if the drive may be dieing, it also has fsck, which checks the filesystems for errors. fsck is run normally during the boot process if it's needed.

---

### Post by Shadius on 2012-05-08
> **losbey said:**
> thats a very good start.... thankyou


will the windows boot loader do something similar ie. will that add the choice of boot to windows 7 or Ubuntu or will it totally ignore Ubuntu ( in this case on a totally different drive )


also will GRUB do the same thing ...take windows of the boot sector


And is there a program will will set youi MBR back to stock or would it be best to use the manufacturers tools  ?

And finally, does Ubuntu have a program that can check out a hard drive to see if its faulty ?

To address your question of if there's a program that will set the MBR back to stock, I've used Boot-Repair many times to do this. 

Also, I've used Ubuntu's Disk Utility to check hard drives. It's very good!

Here's some information about GRUB if you're interested in learning more.
[http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")

---

### Post by Mark Phelps on 2012-05-08
> **losbey said:**
> Let me get it correct...... both Windows and Ubuntu will write boot instructions to the MBR.
Yes and no... Both GRUB and MS Windows modify the MBR; they do not write an OS boot loader into the MBR-- it's not nearly big enough to hold that.

> What happens when you install a windows boot mananger on a hard drive that once had ( or maybe still has ) GRUB on it ?   
Will the PC BIOS recognise both when booting ?  Will one overwrite the other ?
When you install either MS Windows or Ubuntu (and GRUB), both will modify the MBR to point to the appropriate partition containing the boot loader needed.  The BIOS only loads the bootstrap code in the MBR; it knows nothing about OSs.  Since there is a single MBR on a drive, the last installer writing to it wins.

GRUB does not actually boot Windows; nor is Windows capable of booting non-Windows OSs.  GRUB hands over control to the Windows boot loader when you select such an entry in the GRUB menu (or set that to the default).

> Does Ubuntu install anything on other drives after installation ie. you install it on say a SSD and have a normal sata drive. Does it write any data to that normal sata drive when you connect it ?

Depends on what you mean by "drives".  MS uses "drives" to mean partitions, so if you have multiple actual physical DRIVES, Ubuntu will install GRUB, by default, to the first physical drive.

Thus, a problem can arise if your first drive is an SSD containing MS Windows and you install Ubuntu to your second drive (a hard drive).  GRUB will attempt to install itself to the SSD -- which it sees as the first drive.

The way to prevent this problem is to have all other drives disconnected when you install Ubuntu.  That will force GRUB to be installed to the Ubuntu drive. Then, when you reconnect the other drives (including the SSD), continue to boot from the Ubuntu drive.

---

### Post by hyperreal on 2012-05-08
> **losbey said:**
> thats a very good start.... thankyou


will the windows boot loader do something similar ie. will that add the choice of boot to windows 7 or Ubuntu or will it totally ignore Ubuntu ( in this case on a totally different drive )


also will GRUB do the same thing ...take windows of the boot sector


And is there a program will will set youi MBR back to stock or would it be best to use the manufacturers tools  ?

And finally, does Ubuntu have a program that can check out a hard drive to see if its faulty ?

If you are on Ubuntu, you can add the following PPA, which will provide the Boot-Repair software.  This software will restore GRUB.  To add the PPA, use these commands:

```
$  sudo add-apt-repository ppa:yannubuntu/boot-repair
$  sudo apt-get update
$  sudo apt-get install boot-repair
```

To run the software, simply type
```
$  boot-repair
```

You may need to run boot-repair as root if it says permission denied.  While running boot-repair, you will be prompted to choose the recommended boot-repair or a custom boot-repair.  Choose 'recommended', as that is the best way to restore GRUB.  Myself as well as many others have encountered issues while using the custom option.

Hope this helps.  Cheers.

---

### Post by loseby on 2012-05-09
thanks for the replies

Am having major problems with getting a dual boot system up and going  ... mostly Windows starts to boot and load files and then Ubuntu takes over

I just wanted to make sure I knew what was happening before I try again :-)

I Have a new SSD on the way and will use that for Windows and my current SSD will be Ubuntu ( and thats what I am using for this ). So its disconnect Ubuntu drive, install Windows then make my Ubuntu drive the boot drive ...then do a GRUB repair or installation


the dodgy drive can wait till another day

---

### Post by loseby on 2012-05-09
thanks elliptical

I now have GRUB when I boot which is the first thing I wanted

Now its a matter of getting Win7 onto it which is a major problem because as soon as I reconnect the Ubuntu drive Windows wont boot  .......

---

