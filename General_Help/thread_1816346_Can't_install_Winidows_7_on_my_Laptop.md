---
title: "Can't install Winidows 7 on my Laptop"
date: 2011-08-01
forum: General Help
---

### Post by THC420 on 2011-08-01
I had a dual-boot with ubuntu 10.04 and Windows 7 x64 but i wanted to get rid of ubuntu and grub so I thought installing ubuntu over the whole drive and then installing windows 7 over that will fix it but it didn't.
So i got the Ubuntu 10.04 on but the windows cd's won't boot even thought i have 200GB NTFS partition for it. The CD is good works on my other PC, And the CD Drive on my laptop is good because the Ubuntu Live CD works. So basically I want to remove ubuntu and install win 7 but my windows 7 cd won't boot it keep booting into ubuntu. Thanks for helping

---

### Post by cjack2964 on 2011-08-01
Why don't you try opening bios, (usually F10 or F12) and setting the boot location to the DVD drive? All I can think is that maybe grub is doing something funny that won't recognize your DVD drive

---

### Post by THC420 on 2011-08-01
> **cjack2964 said:**
> Why don't you try opening bios, (usually F10 or F12) and setting the boot location to the DVD drive? All I can think is that maybe grub is doing something funny that won't recognize your DVD drive


The DVD is first in my BIOS. Do you have any idea how to get windows on my laptop again?
The Attached image is my partition order. I was hoping i could install Win 7 on the 270GB partition then delete the ubuntu later on

---

### Post by westie457 on 2011-08-01
Windows install discs always override the settings in the bios and try to boot first. The give away that they are booting is a line of text on the screen that says "Press any key to boot from DVD...." You normally have about 5 seconds to decide.

Anyway now for a different approach. Get your LiveCD in the tray and boot into this. When you have a desktop open Gparted, click on Device > Create Partition Table if you want to lose everything on the drive. This will leave you with a lot of unallocated space because you have just wiped out the MBR. 

If there is a partition with something valuable to you and it was not formatted to FAT32 or NTFS you are going to have to lose it. If you set this partition up for dual booting Just delete the others one at a time and move it to where you want.

Remove the cd from the drive replace with the Windows one and hold the power button until the box shuts down. Reboot into the Windows DVD. This time it will run and start you on installing Windows.

---

### Post by THC420 on 2011-08-01
> **westie457 said:**
> Windows install discs always override the settings in the bios and try to boot first. The give away that they are booting is a line of text on the screen that says "Press any key to boot from DVD...." You normally have about 5 seconds to decide.

Anyway now for a different approach. Get your LiveCD in the tray and boot into this. When you have a desktop open Gparted, click on Device > Create Partition Table if you want to lose everything on the drive. This will leave you with a lot of unallocated space because you have just wiped out the MBR. 

If there is a partition with something valuable to you and it was not formatted to FAT32 or NTFS you are going to have to lose it. If you set this partition up for dual booting Just delete the others one at a time and move it to where you want.

Remove the cd from the drive replace with the Windows one and hold the power button until the box shuts down. Reboot into the Windows DVD. This time it will run and start you on installing Windows.

Ok I just tried this made the partition table and then shut it down put the windows cd and now's it's just a black screen this only this blinking "_"<This white line. It's not booting I tried the Win7 CD and the Win Xp cd. Only the Ubuntu Live CD works. I also tried making the empty space into NTFS and that didn't work

EDIT: Right now there's no OS on the laptop. I'm using the live cd to talk

---

### Post by THC420 on 2011-08-01
It's just 300GB of free space on the gparted and it won't boot with my windows cd

---

### Post by akakingess on 2011-08-01
Can you try downloading and burning a copy of DBAN (Darin's Boot And Nuke), just to eliminate any remnants on the drive and to see if it will boot from that CD as well. You could use DBAN to completely clean off the drive and then be back pretty much where you are now, however, it is a step at trying to get to the bottom of this issue. Are you not even seeing the "Press the spacebar now to boot from DVD...." message when booting up the comuter?

---

### Post by westie457 on 2011-08-02
> **THC420 said:**
> Ok I just tried this made the partition table and then shut it down put the windows cd and now's it's just a black screen this only this blinking "_"<This white line. It's not booting I tried the Win7 CD and the Win Xp cd. Only the Ubuntu Live CD works. I also tried making the empty space into NTFS and that didn't work

EDIT: Right now there's no OS on the laptop. I'm using the live cd to talk

Very strange indeed. Let us see what if anything is on your hard drive using Bootinfoscript. Download and usage instructions are available here. [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by THC420 on 2011-08-02
> **westie457 said:**
> Very strange indeed. Let us see what if anything is on your hard drive using Bootinfoscript. Download and usage instructions are available here. [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)



This is form the Result.txt
> ============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System



"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)




I'm going to try DBAN in a few hours

---

### Post by THC420 on 2011-08-02
I was thinking if there's no boot-loader why doesn't the Windows 7 cd boot and overrite it also I don't see the "Press the spacebar now to boot from DVD....". I haven't tried the DBAN yet

---

### Post by Mark Phelps on 2011-08-02
I know it sounds trivial, but let's first make sure we're all using the same terms ...

Win7 does not come on a CD; it comes on a DVD.  Ubuntu comes on a CD.  So, it's possible that your optical drive can read CDs but not DVDs.  To find out, insert some other "DVD" and see if your drive can read it.

IF, in fact, it IS a CD, and it came with the PC, it's likely a WinPE CD, and all that is probably going to do is boot into a menu that will allow you to restore the PC to the factory state -- presuming that you did NOT mess with the vendor-installed Recovery partition.  If that is gone, and it IS a restore CD, then you basically have no way of getting win7 back.

---

### Post by THC420 on 2011-08-02
> **Mark Phelps said:**
> I know it sounds trivial, but let's first make sure we're all using the same terms ...

Win7 does not come on a CD; it comes on a DVD.  Ubuntu comes on a CD.  So, it's possible that your optical drive can read CDs but not DVDs.  To find out, insert some other "DVD" and see if your drive can read it.

IF, in fact, it IS a CD, and it came with the PC, it's likely a WinPE CD, and all that is probably going to do is boot into a menu that will allow you to restore the PC to the factory state -- presuming that you did NOT mess with the vendor-installed Recovery partition.  If that is gone, and it IS a restore CD, then you basically have no way of getting win7 back.


Ok I have tried other DVD's but it counldn't read them but maybe it's because i'm taking out the live cd and putting in the other DVD. Let's say my cd/dvd drive is can't read anything it's possible to install Win 7 thru usb right?

EDIT: I'm still using Live CD to use the internet

---

### Post by westie457 on 2011-08-02
> **Mark Phelps said:**
> I know it sounds trivial, but let's first make sure we're all using the same terms ...

Win7 does not come on a CD; it comes on a DVD.  Ubuntu comes on a CD.  So, it's possible that your optical drive can read CDs but not DVDs.  To find out, insert some other "DVD" and see if your drive can read it.

IF, in fact, it IS a CD, and it came with the PC, it's likely a WinPE CD, and all that is probably going to do is boot into a menu that will allow you to restore the PC to the factory state -- presuming that you did NOT mess with the vendor-installed Recovery partition.  If that is gone, and it IS a restore CD, then you basically have no way of getting win7 back.

Thank you Mark Phelps for pointing that out. I would have posted something like the above earlier had it not been for the fact that work got in the way.

---

### Post by westie457 on 2011-08-02
> **THC420 said:**
> Ok I have tried other DVD's but it counldn't read them but maybe it's because i'm taking out the live cd and putting in the other DVD. Let's say my cd/dvd drive is can't read anything it's possible to install Win 7 thru usb right?

EDIT: I'm still using Live CD to use the internet

Yes it is possible to make a Windows USB install. here is a link for the official tool from Microsoft. [http://www.microsoftstore.com/store/msstore/html/pbPage.Help_Win7_usbdvd_dwnTool](http://www.microsoftstore.com/store/msstore/html/pbPage.Help_Win7_usbdvd_dwnTool)

Which is probably the best one to use. As some one said to me the other day "Windows tools for Windows OS's"

---

### Post by THC420 on 2011-08-03
> **westie457 said:**
> Yes it is possible to make a Windows USB install. here is a link for the official tool from Microsoft. [http://www.microsoftstore.com/store/msstore/html/pbPage.Help_Win7_usbdvd_dwnTool](http://www.microsoftstore.com/store/msstore/html/pbPage.Help_Win7_usbdvd_dwnTool)

Which is probably the best one to use. As some one said to me the other day "Windows tools for Windows OS's"


Done I got Windows 7 working thru USB Thanks.

---

