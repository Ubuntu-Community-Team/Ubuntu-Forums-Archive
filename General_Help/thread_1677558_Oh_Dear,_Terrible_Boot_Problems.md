---
title: "Oh Dear, Terrible Boot Problems"
date: 2011-01-28
forum: General Help
---

### Post by Taliathion on 2011-01-28
A fairly devastating error here.
I was doing some editing of my partitions, and I was messing around with some empty space, and hit a BSoD.

Long Story short, the partition containing my Ubuntu install, and therefore GRUB is corrupted.
My boot now says:

error: unknown filesystem.
grub rescue>


And no commands work, they all return unrecognized command.
So... I'm completely locked out.
~Edit- ACTUALLY, ls returns all of my partitions: 
(hd0) (hd0,7)(hd0,6) (hd0,5) (hd0,4) (hd0,2) (hd0,1) (hd1) (hd1,1)

If it's any help, I have a spare VL install drive for XP around here, so I could boot into it and install and fix from within XP maybe?

Thanks so much,
Taliathion

---

### Post by Rubi1200 on 2011-01-29
Hi,

I suggest the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Taliathion on 2011-01-29
I'm afraid I can't.
When I boot using a 10.10 live-USB, it goes to the usual live menu, but when I tell it to boot and run from the usb, it runs into problems. 
At first it loads fine, with no error messages, but once it phases into and passed the five-dot loading menu, the screen locks up with distorted horizontal white and black bars with random pixels strewn about.
But also weird, the sound continues to play normally.
Also, I don't believe there was a boot without any changes option.

And also, perhaps I was not clear enough in the main post, I don't want to make anyone that is helping me's job harder.
The only important things on my Ubuntu install were some documents, and I already have those backed up on windows 7. I'm completely fine with scrapping whatever's left and just removing grub to re-allow access to Windows 7, and then re-installing ubuntu.

---

### Post by TheHackOps on 2011-01-29
Just re-image the partition it will be easier

---

### Post by Rubi1200 on 2011-01-29
The issue you described is probably related to your graphics card; there are ways around it.

If you want me to help with that, just ask.

As to restoring the ability to boot Windows again, see here:
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

---

### Post by Taliathion on 2011-01-29
1. I have a laptop, and had no idea something like this would happen, so I had not prepared any type of recovery disk.

2. Re-image a partition without access to any operating system?


And if it allows me to enter ubuntu to continue with the steps in your first post Rubi, then yes, I would like to fix the graphical errors.

Video Card: Nvidia GeForce GTS 360m

---

### Post by Rubi1200 on 2011-01-29
To get the LiveUSB booting, this is what you can do.

As it starts and you see the screen to select language and choose the option to try Ubuntu without changes, after that hit F6 immediately.

You will see a menu at the lower right-hand of the screen with various options; choose nomodeset and then Enter to boot.

If this works and you get to the live desktop, continue with the instructions above for the boot info script please.

---

### Post by Taliathion on 2011-01-29
> **Rubi1200 said:**
> 
You will see a menu at the lower right-hand of the screen with various options; choose nomodeset and then Enter to boot.



I don't have a try without changes choice, but when I get to the live menu, I CAN press escape and get a commandline with
boot:
But when I enter nomodeset it says it cannot find the kernel image for nomodeset (or something similar)

---

### Post by Rubi1200 on 2011-01-29
When you are at the live menu press F6 followed by Esc.

Do you see a line that looks like this:
> **file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --**

If yes, then remove quiet splash and add nomodeset so it looks like this:
> **file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz nomodeset --**

Enter to boot.

---

### Post by samskiter on 2011-01-29
appologies for hijacking, but i have a similar problem at the minute. was getting the grub rescue prompt too.

Rubi, if you could have a look at my (only) thread and offer any advice on recovering partitions with tesdisk it would be much appreciated

---

### Post by Taliathion on 2011-01-29
f6 causes the screen to go black and come back instantly, so it flashes you could say, but that doesn't change anything, escape still brings me to-
boot:

---

### Post by Rubi1200 on 2011-01-29
Did you change the boot priority in BIOS to boot from the USB drive?

If Ubuntu won't work, you can try something called Slax (I believe it is possible to put it on a USB stick).
[http://distrowatch.com/table.php?distribution=slax](http://distrowatch.com/table.php?distribution=slax)

---

### Post by Taliathion on 2011-01-29
Naw, but my computer has an alternate start system, I can press escape at start-up and choose where I want to boot from, and when I choose my USB it goes to Live menu, but nothing you've said works.

And what would I do with slax? Boot into it and do the steps you've proposed I do in Ubuntu?

---

### Post by Rubi1200 on 2011-01-29
Do you know which partition Ubuntu is installed on?

You can try the commands from this thread to boot:
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

---

### Post by Taliathion on 2011-01-29
> **Rubi1200 said:**
> Do you know which partition Ubuntu is installed on?

About that...
The issue is, the BSoD occurred while it was preforming an action to some empty space... but I don't know the name of the partitions, so anything could have happened to the Ubuntu partition. I'm not even sure if it is still technically **Installed.** 
An obvious side effect is that I have no idea where it would be installed if it still is.
Do you have an instant messaging account? Really any is fine, but it seems to me it would be easier than communicating through the forum.
Regardless, I'm not sure I can follow the linked thread, and don't know what I should be doing.
Any other ideas for fixing the graphical errors?

---

### Post by Rubi1200 on 2011-01-29
This is what you need to do:

Start the computer normally; it will go to the grub rescue prompt.

Type ls as before to list the partitions.

Then,```
 ls (hd0,1)/boot/grub
```

do this for each entry until you locate the right one.

My guess is that it will be 4, 5, 6, or 7 (from what you posted above).

For example:```
 ls (hd0,4)/boot/grub
```

Let me know when/if you find the right partition.

(off:topic; don't have/use IM)

---

### Post by Taliathion on 2011-01-29
Erm, all of them return unrecognized filesystem.
:O
As in, even the empty one, the blank space.

---

### Post by Taliathion on 2011-01-29
Also, it occurs to me, why would the livecd have graphical errors if 10.10 worked normally without any config before?

---

### Post by Rubi1200 on 2011-01-29
It shouldn't; which is why this is problematic.

Okay, back a step:

try the ls command now like this (substitute the right partition and work your way through):

```
ls (hd0,1)/
```Look for any folders such as /home, /bin, /boot  etc.

Unless the system was completely fried, *something* must be there (we just have to try and find it).

I still think that if you can, try Slax as mentioned before (put it on a USB with something like [UNetbootin]("http://unetbootin.sourceforge.net/")).

---

### Post by Taliathion on 2011-01-29
All of them return unknown filesystem
I think Ubuntu is totally destroyed...
Once I get Slax, should I just follow the original instructions? 
Or would that be useless because Ubuntu is scrapped?
Because I can live with no Ubuntu for now, I just need to get past Grub to get to Windows Loader.

---

### Post by Rubi1200 on 2011-01-29
If you can get Slax to boot the computer, then run the boot info script I mentioned with one difference:

```
bash ~/Desktop/boot_info_script*.sh
```
This command will suffice since you will have a root prompt on Slax by default.

---

### Post by Taliathion on 2011-01-29
!!!
Wait!
I went back to the Live USB menu, and pressed tab on the entry:

Boot from first hard disk

and it shows it's menu entry!

it shows
> .localboot 0x80

Shouldn't there be a way to edit that to boot into whatever disk has Windows 7 and do repair from it?

---

### Post by Taliathion on 2011-01-29
Also, I changed the default 0x80 and added a one to see what error it gives me, and it failed of course, but it shows

Boot failed: please change disks and press a key to continue
ERROR: idle with IF=0
0000 980F 06E7 0A50 F000 0080 0000 0180 0001 070B 5E20 0020 0000 5FDF 00F0 0000

The presence of the 0080 makes me think these are the disks in Hex format.

Can I use one of these to boot into Windows?

~Edit:
Hex to plaintext comes up with lots of unreadable symbols, so idunno if that's it, but is this worth looking in to?

---

### Post by Rubi1200 on 2011-01-29
> .localboot 0x80is the designation for the hard-drive itself and I really don't know if you can change/append something that will help you.

I still think Slax is the route to take unless someone else knows another way to get you into one of the partitions.

You might also want to take a look at Testdisk:
[http://www.cgsecurity.org/wiki/TestDisk_Livecd](http://www.cgsecurity.org/wiki/TestDisk_Livecd)
[http://www.cgsecurity.org/wiki/Running_TestDisk](http://www.cgsecurity.org/wiki/Running_TestDisk)
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by Taliathion on 2011-01-29
I'm downloading Slax now, will be done in a moment, but what is the point if all it will do is confirm that ubuntu is destroyed?

And I AM able to edit the 0x80 thing, so if I can find the designation for my HD's/Partitions, can't I just use those to boot into it?

---

### Post by Taliathion on 2011-01-29
Oh good, my hd isn't destroyed!
But I don't see any record of Ubuntu here...?

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 1640. But according to the info from fdisk, 
                       sda6 starts at sector 556869632.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x76692ca8

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    40,965,749    40,963,702   c W95 FAT32 (LBA)
/dev/sda2          40,966,144   285,159,423   244,193,280   7 HPFS/NTFS
/dev/sda3         285,161,470   642,861,055   357,699,586   f W95 Ext d (LBA)
/dev/sda5         285,161,472   556,867,991   271,706,520   7 HPFS/NTFS
/dev/sda6         556,869,632   639,242,239    82,372,608   7 HPFS/NTFS
/dev/sda7         639,246,336   642,861,055     3,614,720  82 Linux swap / Solaris
/dev/sda4         642,861,056   882,397,183   239,536,128   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8065 MB, 8065646080 bytes
8 heads, 32 sectors/track, 61535 cylinders, total 15753215 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32    15,753,214    15,753,183   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mmcblk3p1   0000-0000                              vfat                                     
/dev/sda1        3C98-AC5D                              vfat       RECOVERY                      
/dev/sda2        0E1EBEA01EBE7FEF                       ntfs       OS                            
/dev/sda4        7EF4DEB7F4DE70BF                       ntfs       DATA2                         
/dev/sda5        36CAC19BCAC1582F                       ntfs       DATA                          
/dev/sda6        A4A40E0AA40DE022                       ntfs       New Volume                    
/dev/sda7        9f1418b0-0a37-4437-b865-59810debe184   swap                                     
/dev/sdb1        6ABC-7496                              vfat       PENDRIVE                      

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw,si=7d70c317,xino=/mnt/live/memory/xino/.aufs.xino,nowarn_perm)
/dev/sda1        /mnt/sda1                vfat       (rw,noatime,quiet,umask=0,check=s,shortname=mixed)
/dev/sda2        /mnt/sda2                fuseblk    (rw,noatime,allow_other,blksize=4096)
/dev/sda4        /mnt/sda4                fuseblk    (rw,noatime,allow_other,blksize=4096)
/dev/sda5        /mnt/sda5                fuseblk    (rw,noatime,allow_other,blksize=4096)
/dev/sda6        /mnt/sda6                fuseblk    (rw,noatime,allow_other,blksize=4096)
/dev/sdb1        /mnt/sdb1                vfat       (rw,noatime,quiet,umask=0,check=s,shortname=mixed)
/dev/mmcblk0p1   /mnt/mmcblk0p1           vfat       (rw)
/dev/mmcblk1p1   /mnt/mmcblk1p1           vfat       (rw)
/dev/mmcblk2p1   /mnt/mmcblk2p1           vfat       (rw)
/dev/mmcblk3p1   /mnt/mmcblk3p1           vfat       (rw)


=================== sdb1: Location of files loaded by Grub: ===================


   7.8GB: boot/initrd.gz
   7.8GB: boot/vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  77 23 9f 2b 3e 84 66 17  bb f1 d7 db fd 40 4a 53  |w#.+>.f......@JS|
00000010  bc 14 e2 17 23 25 8a 6a  1a cb eb 7e 70 86 36 36  |....#%.j...~p.66|
00000020  47 37 44 f8 90 ff d6 c4  a9 65 6f 3c 04 ad af 57  |G7D......eo<...W|
00000030  e6 eb 03 29 1f 09 26 96  d5 8b d5 00 58 2c 52 0b  |...)..&.....X,R.|
00000040  03 d5 cc b6 3d 84 75 b2  5a 6f 5c b8 6d 99 0d 14  |....=.u.Zo\.m...|
00000050  1a 1b 46 e5 9a c0 5a df  53 84 7b cd 04 6b b0 05  |..F...Z.S.{..k..|
00000060  de 7c 88 89 7e ed 33 10  1e 61 04 37 5b 53 e8 04  |.|..~.3..a.7[S..|
00000070  97 e9 5c 2b 85 8d 86 c8  f6 d9 c0 a7 d8 bb c3 c5  |..\+............|
00000080  1a d8 17 4b e0 f6 bf 10  b7 0e 2d 7f a2 1a b5 cd  |...K......-.....|
00000090  03 af a0 65 1b f8 b3 7d  16 27 b8 84 99 cb 5c 79  |...e...}.'....\y|
000000a0  90 ca e5 1d ca e1 36 d5  4f f1 1e 3e 60 e3 5f 83  |......6.O..>`._.|
000000b0  9a 3d ac db 42 0b 46 26  e1 23 d7 7f a4 ab 09 22  |.=..B.F&.#....."|
000000c0  6f 78 f6 7e ca c0 89 c1  e3 da a5 be 6b fd 34 72  |ox.~........k.4r|
000000d0  3d 8a fa 75 06 55 e7 39  07 29 d0 52 b7 76 00 36  |=..u.U.9.).R.v.6|
000000e0  76 52 ca 40 3c f8 3b a8  d1 05 db 72 2b ea 9d 6a  |vR.@<.;....r+..j|
000000f0  10 16 f7 1f ed 25 01 f6  83 71 2e e3 d4 8b 88 d5  |.....%...q......|
00000100  a5 20 fb b4 86 de 4f 51  75 f7 71 27 b0 c9 7b 6b  |. ....OQu.q'..{k|
00000110  80 5d 3c 46 ef 61 57 28  9e 46 72 49 8a eb b3 15  |.]<F.aW(.FrI....|
00000120  60 97 e4 b6 46 28 e8 76  b9 93 b1 78 2b 19 a8 c2  |`...F(.v...x+...|
00000130  aa 3b 38 d8 01 cb 5b 9c  a3 89 84 05 fa af 83 7a  |.;8...[........z|
00000140  0e e3 3b bd 77 da a8 9f  8c 62 8b f6 4f f7 dc b5  |..;.w....b..O...|
00000150  98 85 dd 58 79 56 8e 84  06 4c fa 5e 32 c2 73 92  |...XyV...L.^2.s.|
00000160  17 bc bd 66 94 7c 94 18  89 f9 4b dd 2a 13 a5 d9  |...f.|....K.*...|
00000170  c0 b5 af ba 46 60 86 dc  25 43 f3 03 fd dc c9 8f  |....F`..%C......|
00000180  90 46 31 7d 74 24 d2 a1  02 c1 da 62 b3 8d f4 1b  |.F1}t$.....b....|
00000190  da 43 0e a1 1a 15 ff 7d  44 98 82 8c 1b 80 89 9d  |.C.....}D.......|
000001a0  e8 dc e8 f3 cd c2 4d ac  68 8e 06 b1 97 c9 a5 ce  |......M.h.......|
000001b0  2f f5 2d 26 c2 ed 78 4b  37 93 94 00 77 c3 00 fe  |/.-&..xK7...w...|
000001c0  ff ff 07 fe ff ff 02 00  00 00 98 e9 31 10 00 fe  |............1...|
000001d0  ff ff 05 fe ff ff 9a e9  31 10 68 ee e8 04 00 00  |........1.h.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

File descriptor 11 (socket:[12918]) leaked on lvscan invocation. Parent PID 12357: /bin/bash
mdadm: No arrays found in config file

```

---

### Post by Taliathion on 2011-01-29
What now, good sir?

---

### Post by Rubi1200 on 2011-01-29
This was from Slax right?

Slax seems to be able to get into things when other live distros cannot; keep it safe as you never know when you might need it again.

Okay, this is my assessment of the situation:

Whatever caused this has damaged the Ubuntu installation which I assume was on sda6 and appears to have wiped it out because it says the file-system is NTFS.

Testdisk is one option to try and recover the partitions/data.

Another option is to reinstall the Windows bootloader so you can boot Windows again and then reinstall Ubuntu.

To restore Windows bootloader:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

There is also another way; install a Windows-like bootloader called lilo.

This can normally be done from a live distro, but I don't know if it is available on Slax.

Let me check and get back to you on that one.

---

### Post by Taliathion on 2011-01-29
Oh good!
Yeah, I'm backing up Slax for sure.
~Edit: Removed dumb question, I should have read the rest of the page :P

---

### Post by Taliathion on 2011-01-29
And also, Slax isn't accepting my wireless card, so I can't like, download anything, I just copy it through SD.
And I can't make / on it, or ~, the keyboard is wrong, but there aren't any other options under settings.

---

### Post by Rubi1200 on 2011-01-29
I took a quick look and as far as I can tell the package I wanted is not available on Slax.

How was Windows installed? Do you have a recovery medium?

I believe you can also use Testdisk to achieve the same thing, restore the ability to boot Windows.

---

### Post by Taliathion on 2011-01-29
OEM install, no recovery medium available, but the link you posted had ANOTHER link, with .torrents for recovery disks.
Working on getting them to work.

---

### Post by oldfred on 2011-01-29
Do you have nvidia LVM running?

Script shows this and others which looks like a LVM:
/dev/mmcblk0p1 

You can also use supergrub to restore boot, it now have several versions, grub, grub2 and one that restores grub2. I think they all will restore or at least boot windows.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/AutoSuperGrubDisk](http://www.supergrubdisk.org/wiki/AutoSuperGrubDisk)

Did you copy a windows partition? It looks like you copied a windows partition to where Ubuntu was.

---

### Post by Taliathion on 2011-01-29
I understood like 1/4th of that...
But anyway, I burned a win7 recovery iso to a CD and when I boot and tell it to load from cd?

WTF~ 
Grub takes back over and says:

error: unknown filesystem
grub rescue>

Why can't I boot from this?
Was I supposed to burn the .iso or the files within?
I burned the iso, but it cant boot from it.
Should I burn the files on the .iso instead?

---

### Post by Taliathion on 2011-01-29
Well.
No matter how I burn or format this, It doesn't boot, grub takes over.

also, BUMP.

Weird server crash.

---

### Post by Taliathion on 2011-01-29
So, how should I go about repairing Windows 7 with access only to Slax?

---

### Post by oldfred on 2011-01-29
You do not burn the ISO file as the ISO file. You need to burn the ISO with software that recogizes that it is an ISO and converts it to all the files including the booting.

This is one of the recommended software to use with windows. You want to write image or burn image so it is properly converted.
[http://infrarecorder.org/](http://infrarecorder.org/)

---

### Post by Taliathion on 2011-01-29
Herp. 
I knew that -.-
I guess this issue is just messing with my head.
Thanks so much, if it works, you are my saviour.
And Rubi!
You sir ~Edit (Or madam!), are a ***Saint.***

---

### Post by Taliathion on 2011-01-29
First try had a "corrupt file." 
Trying again at a low write speed with a high-quality dvd.

---

### Post by Taliathion on 2011-01-29
Got it all running and got into the repair menu.
First, it didn't find my install.
So I continued
did bootrec.exe /fixmbr and /fixboot
restarted
got:
BOOTMGR is Missing
Press any key to restart
Did so.
Booted from CD
It found my install.
Did auto system-repair.
Found errors, could not fix. (Will post if necessary)
Did fixmbr and fixboot
No errors.
Restart
BOOTMGR is missing.

...?

---

### Post by Taliathion on 2011-01-29
Nevermind, my impatience fixed it!
The guide in the links told me NOT to select the OS.
But I did.
And it did an auto-repair.
And WORKED
Everything boots and works as normal!
Solved.
And:
Rubi~ THANK YOU SO MUCH. The time and effort you put into this were astounding.

Oldfred~ Thanks muchly for kicking my brain into action, I burn .iso's often but didn't think about that for even a second!

---

### Post by oldfred on 2011-01-29
I found CDs at slowest speed allowed works best.

There is a way to install a windows style boot loader called lilo. It is another boot system but the part in the MBR works just like windows in that it looks for the partition with the boot flag and jumps to that partition to keep booting. 

Not sure if slax includes lilo but many linux repair CDs do just to fix windows.

This may not work without downloading lilo and I have not used slax so I do not know the specifics on how to download in it.

sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

---

### Post by Rubi1200 on 2011-01-30
> **Taliathion said:**
> Nevermind, my impatience fixed it!
The guide in the links told me NOT to select the OS.
But I did.
And it did an auto-repair.
And WORKED
Everything boots and works as normal!
Solved.
And:
Rubi~ THANK YOU SO MUCH. The time and effort you put into this were astounding.

Oldfred~ Thanks muchly for kicking my brain into action, I burn .iso's often but didn't think about that for even a second!
No problem, you are more than welcome for the help :-)

Thanks, too, to oldfred for jumping in and helping out.

(off:topic; Rubi is a Sir :lolflag:)

---

