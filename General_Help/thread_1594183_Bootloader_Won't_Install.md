---
title: "Bootloader Won't Install"
date: 2010-10-12
forum: General Help
---

### Post by abigailrf on 2010-10-12
I installed Ubuntu no problem, except for when it came to picking the location for GRUB2 to go, the bootloader. It error'd out on me, and would not let me select a single location, so I clicked continue without, and I'd install it manually. Well, once it got to the manual part, it said everything was kosher, but when I reboot, I am greeted with a black terminal screen.

It tells me to hit tab for commands. What exactly did I do wrong, and how may I fix this? Do I need to reinstall ubuntu? I'm running off the LiveCD right now, and it's ok, but I really hate having to use a CD to even boot up.

Thank you!

---

### Post by Peter09 on 2010-10-12
If its booting OK, then it may be a graphics driver issue. Can you clarify wether you reach the login screen.
 
Also - try holding the shift key during boot. This should get you to the grub menu. From there select recovery mode and when it gets to the munu try - the reconfigure graphics option.
 
This all assumes that the system is booting correctly.

---

### Post by Peter09 on 2010-10-12
Edit: having said the 'above' and then re-reading your text I suspect that grub is not loading the O/S. This can be solved from the LiveCD - but I am not sure of the full command chain so I will leave to someone else to provide the information - rather than give you something that may do unfixable damage.

---

### Post by abigailrf on 2010-10-12
I'm not even reaching the login screen. It gets so far as to booting past my bios loading, and such, and then black terminal-like screen that states the grub build up top, some instructions on hitting tab, etc.

And then Grub>

I hit tab and get my list of commands, and usually I just hit reboot. In the live session, can I try installing the graphics driver it recommends and see if that might fix it?

Because when I type boot, or anything of that type, it says no kernel. Which is confusing, because I check my location it's installed in, and it's all there. Well, mostly. I'm actually missing the grub.cfg file...it's not in there. Even though when I followed the instructions I was linked to by a friend, it said it was all set.

(Edit: But thank you for trying :) )

---

### Post by Rubi1200 on 2010-10-12
You need to use the LiveCD and post the results of the bootscript linked at the bottom of my post.

If there is/was a problem with the GRUB install, the results should tell us and make offering solutions easier.

Thanks.

---

### Post by garvinrick4 on 2010-10-12
It sounds like you just do not have grub in mbr which is real easy to fix. Give the results of 
the script as the user in front of me stated and it will be fixed.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download that to your desktop and then open a terminal and copy and paste:
 ```
sudo bash ~/Desktop/boot_info_script*.sh 
```

It is a long text file that will be on your desktop. Open it and highlight 
the whole thing and then hit the # sign in the right of your message box and 
it will make it easier to read. Takes about 10 seconds to do.

---

### Post by abigailrf on 2010-10-12
I just wanted to say, the date is off because I haven't configured it yet lol.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   300,292,095   300,290,048  83 Linux
/dev/sda2         300,294,142   312,580,095    12,285,954   5 Extended
/dev/sda5         300,294,144   312,580,095    12,285,952  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 319.4 GB, 319370035200 bytes
255 heads, 63 sectors/track, 38827 cylinders, total 623769600 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   623,769,599   623,767,552   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048   625,139,711   625,137,664   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        a53166e4-90da-4d97-99ad-cebf93a7aec0   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        1e428b6a-6fa3-495b-9196-ba30a0df4dec   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        8A6402646402537D                       ntfs       HP SimpleSave                 
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        74A4F3DFA4F3A232                       ntfs       New Volume                    
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/a53166e4-90da-4d97-99ad-cebf93a7aec0 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdc1        /media/New Volume        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1        /media/HP SimpleSave     fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sr0         /media/apt               iso9660    (ro)


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=1e428b6a-6fa3-495b-9196-ba30a0df4dec none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  38.7GB: boot/grub/core.img
    .8GB: boot/initrd.img-2.6.35-22-generic
    .3GB: boot/vmlinuz-2.6.35-22-generic
    .8GB: initrd.img
    .3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  0e ff 0e 77 2c ef 71 14  fd 39 ff 1c f3 39 d0 70  |...w,.q..9...9.p|
00000010  0a ff 39 ff 39 01 f1 39  00 00 07 70 02 21 00 f1  |..9.9..9...p.!..|
00000020  1e 39 30 35 36 34 00 32  36 41 30 37 46 42 31 10  |.90564.26A07FB1.|
00000030  33 44 34 44 90 00 41 42  32 08 46 45 30 80 7c 41  |3D4D..AB2.FE0.|A|
00000040  33 46 b8 31 d0 04 76 6b  29 ff 1e f7 1e 73 79 00  |3F.1..vk)....sy.|
00000050  73 74 65 6d 33 32 5c 4d  00 55 49 5c 30 34 30 39  |stem32\M.UI\0409|
00000060  5c c0 6d 73 63 6f 72 65  60 87 a2 9f bb d2 06 7f  |\.mscore`.......|
00000070  6e 00 7f 2a b0 06 71 0b  e0 7f 6e 06 00 71 0b 79  |n..*..q...n..q.y|
00000080  6e 42 42 41 46 43 08 41  35 32 b0 b7 30 33 39 38  |nBBAFC.A52..0398|
00000090  00 34 35 38 32 41 39 33  44 00 45 35 32 36 37 37  |.4582A93D.E52677|
000000a0  36 41 6a 36 f5 4d 42 d0  07 f0 30 14 71 05 00 05  |6Aj6.MB...0.q...|
000000b0  30 50 f0 30 06 b0 e6 9e  00 40 e0 df 9e 00 d0 f0  |0P.0.....@......|
000000c0  ff 14 c1 0a ff 33 d9 f3  33 d8 af ff 14 71 09 74  |.....3..3....q.t|
000000d0  41 03 30 00 01 f1 14 41  46 31 39 32 37 46 20 32  |A.0....AF1927F 2|
000000e0  39 39 46 38 80 d9 34 33  80 38 44 44 39 34 33 41  |99F8..43.8DD943A|
000000f0  50 4f a0 46 43 38 32 31  73 9d 39 ff 14 cf ff 33  |PO.FC821s.9....3|
00000100  ff 33 f6 33 02 16 72 63  a3 b5 d2 07 cf ff 15 ff  |.3.3..rc........|
00000110  15 a0 0f f2 77 c0 92 7f  84 71 0c 8e d8 90 04 71  |....w....q.....q|
00000120  6d 72 21 35 43 37 a0 c2  00 46 43 37 37 44 46 37  |mr!5C7...FC77DF7|
00000130  30 a0 34 32 41 30 36 70  a9 38 50 cd 60 46 38 44  |0.42A06p.8P.`F8D|
00000140  35 36 75 84 31 03 c8 9e  f3 7f 9d ff e5 f3 e5 f1  |56u.1...........|
00000150  17 50 57 b0 17 e0 71 9e  00 80 ae ff 17 c1 0c ff  |.PW...q.........|
00000160  17 b1 f3 17 e8 0c 31 ff  e4 00 03 8a 41 03 0b 30  |......1.....A..0|
00000170  00 f2 17 37 c0 4a 31 30  31 39 00 36 32 34 37 32  |...7.J1019.62472|
00000180  43 34 32 04 38 45 80 f1  36 41 35 35 43 a0 46 41  |C42.8E..6A55C.FA|
00000190  34 45 39 75 0b da f0 02  74 a0 87 75 0b 00 7f f1  |4E9u....t..u....|
000001a0  7c f1 f1 56 88 03 70 13  f1 0b 58 01 8c 00 00 36  ||..V..p...X....6|
000001b0  2c 31 01 31 00 71 01 a0  f0 c2 7d b7 00 68 00 fe  |,1.1.q....}..h..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 78 bb 00 00 00  |...........x....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

---

### Post by Quackers on 2010-10-12
There should be a /boot/grub/grub.cfg before the other entries in the Boot files/dirs: section of sda1 but there isn't.
As you are in a live cd at the moment have a look at the following link and follow the instructions from where it says Why chroot in RED.
FYI your installed system is in sda1 and the install of the bootloader would go in sda
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by abigailrf on 2010-10-12
> **Quackers said:**
> There should be a /boot/grub/grub.cfg before the other entries in the Boot files/dirs: section of sda1 but there isn't.
As you are in a live cd at the moment have a look at the following link and follow the instructions from where it says Why chroot in RED.
FYI your installed system is in sda1 and the install of the bootloader would go in sda
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

So, when Chroot-ing, I want to mount into sda1 then? Since it is where my real installation is.

---

### Post by Quackers on 2010-10-12
Yes, that's right.

---

### Post by abigailrf on 2010-10-12
> **Quackers said:**
> Yes, that's right.

You sir, are my hero. Thank you tons, I am back up and running :)!

---

### Post by Quackers on 2010-10-12
Very, very nice indeeeeeeeeeed :-)

---

