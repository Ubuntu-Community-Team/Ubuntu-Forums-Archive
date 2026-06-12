---
title: "Grub mess with winload.exe?"
date: 2010-11-03
forum: General Help
---

### Post by TurtleKing on 2010-11-03
I disconnected my ubuntu hard drive from the motherboard to determine whether it was the cause of a random restart problem on the computer, but that is another story. Anyways, I now tried to boot from the vista hard drive and received a message that grub was missing. So I went ahead and used the Ubuntu Live CD, and put the main bootloader that windows normally ran. Now, I get the message that the winload.exe file is either missing or corrupt and it will not let me through. I read the recommendation of using the Vista CD you purchased, but I can't find it. So I tried and downloaded the recovery tool boot file which you are suppose to burn to a CD in order to run it during your computer's startup. And I find out we are out of CDs.

I will unfortunately have to reconnect the other hard drive, and so forth to access the vista/ubuntu driver.

My question is why is this winload.exe file corrupted or removed after installing grub? I know the windows boot loader won't recognize Ubuntu, so you need some type of grub boot loader in order to use it. Does grub remove this file from vista?

Also, does anyone know if I can download this winload.exe file to put in win32 or system32 (i think it's called), so I can manually move it there with Ubuntu Live CD? 

I am a little frustrated with both Grub and Vista right now. At Grub for removing or corrupting the file, and Vista for not offering the winload exe file instead of a recovery tool to burn to a CD.:mad:

---

### Post by Quackers on 2010-11-03
I think it may be a good idea if you can boot from the Ubuntu Live cd and choose "try Ubuntu". When the desktop loads, and making sure you've got an internet connection, please go to the site below and download the boot script to your DESKTOP and run it in a terminal using the command given on the first page of that site.
This will produce a results.txt file on your desktop. Please copy the contents of that file and paste it in between CODE tags in your next post. For CODE tags click on New Reply then on the # symbol in the toolbar
This will give a clearer idea of what is where on your system. Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by TurtleKing on 2010-11-03
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Testdisk is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   976,768,064   976,768,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        623C3D833C3D52F1                       ntfs                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
```
Please let me know if there is some info that might be useful for malicious hackers, scamers, etc.

---

### Post by Quackers on 2010-11-03
I've never used testdisk, but appears to be installed in the mbr of your sda. If you have a Windows repair disk you should boot from it and select the startup repair option (it may need to be run 3 times, but I suspect not in your case). This should make Windows bootable.

---

### Post by TurtleKing on 2010-11-03
> **TurtleKing said:**
> I read the recommendation of using the Vista CD you purchased, but I can't find it. So I tried and downloaded the recovery tool boot file which you are suppose to burn to a CD in order to run it during your computer's startup. And I find out we are out of CDs.

Thanks for trying to help me solve this problem. (Sorry for quoting, but I am a little bit worn out from the several computer test I been doing the past couple of days, and now this problem.)

---

### Post by Quackers on 2010-11-03
There is a way to make a Windows repair usb stick but sadly I don't have a link to it.
You can also install Lilo from a Ubuntu Live CD which does the same thing. Thanks to coffeecat :-)

[http://ubuntuforums.org/showpost.php?p=10056077&postcount=5](http://ubuntuforums.org/showpost.php?p=10056077&postcount=5)

---

### Post by joshruehlig on 2010-11-03
As everyone else said.

You installed grub mbr on the vista hard drive. It then tells the computer to look on the ubuntu partition on the ubuntu harddrive (no longer there) for grub info. You need a vista repair cd/usb.

With windows 7 they have (legal) iso's of Windows 7 on the internet that you can just use unebootin to install to a usb stick. With vista I dont think they do (legally...).

---

### Post by TurtleKing on 2010-11-03
> **joshruehlig said:**
> As everyone else said.

You installed grub mbr on the vista hard drive. It then tells the computer to look on the ubuntu partition on the ubuntu harddrive (no longer there) for grub info. You need a vista repair cd/usb.

With windows 7 they have (legal) iso's of Windows 7 on the internet that you can just use unebootin to install to a usb stick. With vista I dont think they do (legally...).
*sigh* No blank CD no fix. As for the lilo, is that a boot menu program or a repair for windows boot menu program? 

I wonder why they don't have grub install a copy on the other partitions rather than just the one Ubuntu is using? But then again why is Microsoft such an *** about not opening other OS in their boot loader so people wouldn't need to install grub in the first place? Gotta love the greedy thinkers. lol

---

### Post by wilee-nilee on 2010-11-03
Lilo is just another bootloader that plays nice with windows.

---

### Post by TurtleKing on 2010-11-03
Lilo does not seem to be working either. I am going to try with the Ubuntu Hard Drive this time to see it works. This has really gotten annoying. Now I have the ubuntu hard drive connected, but I cannot access it either.

---

### Post by wilee-nilee on 2010-11-03
> **TurtleKing said:**
> Lilo does not seem to be working either. I am going to try with the Ubuntu Hard Drive this time to see it works. This has really gotten annoying. Now I have the ubuntu hard drive connected, but I cannot access it either.

So going to a store and buying a cd is just out of the question. This would be fixed with one command from the recovery disc repair command line. Here is the whole set the highlighted one is your friend.
1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
**BootRec.exe /fixmbr** (#updates MBR master boot record...do not run if you still want grub)
chkdsk /r
BootRec.exe /FixBoot (#updates PBR partition boot)
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

---

### Post by wilee-nilee on 2010-11-03
Boot the live cd and run the script with the W7 and Ubuntu HD plugged in this may be a easier fix by just putting the grub2 bootloader on the correct HD and having it read to boot first.

You mention the Ubuntu HD originally but the first script does not show it, as it was unplugged.

---

### Post by TurtleKing on 2010-11-04
I will mark this thread solved as this can technically be solved with a blank disk and a download of a windows recovery CD to burn to your blank CD. In addition, there is also the option of remembering where you left the installation CD that came with Vista or Win7. If you don't have a blank CD, and you forgot where your Vista/Win7 installation CD is located like me, then I sure hope you can get a ride to a nearby store where blank CDs are sold. lol

---

