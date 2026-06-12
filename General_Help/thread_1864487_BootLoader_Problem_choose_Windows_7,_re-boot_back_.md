---
title: "BootLoader Problem: choose Windows 7, re-boot back to choices"
date: 2011-10-19
forum: General Help
---

### Post by lianazaman on 2011-10-19
Hi,

Been trying Ubuntu 11.10, and it's awesome (if not that there are some schoolwork I need to do with Windows). I tried to boot into Windows 7, but each time I choose Windows 7, it re-boot back to the choices. Means I can only enter Ubuntu, but not Windows 7, even if I choose that in the menu.

I'm not sure, but I think it's because I installed the bootloader options on the Windows 7 partition ( I thought if I do that, that means by default it will boot into Windows 7 if no choice was made. I was wrong.)

At first I thought of straight using Repair Disc Image (Windows), but that is usually been used when uninstalling Ubuntu to resolve the startup problem after uninstalling. I still want to use my Ubuntu though.

Any other alternative?

---

### Post by garvinrick4 on 2011-10-19
If you want to know all about what is going on with your drive and what is there and not there and why
no boot do this below and post results so we can fix you up.
From Ubuntu download the bootscript from link
below to DESKTOP. Right click on and choose to extract with Archive Manager.
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/") 

Then run this line of code in terminal. [ctrl/alt/t]  (copy and paste it in to terminal hit enter)
     

     ```
sudo bash ~/Desktop/boot_info_script.sh
```Will make a RESULTS.txt file on Desktop open and copy and paste in a Message box and highlight
whole thing (is Long) and hit # in upper right of message box and will put in nice little box to read from.

---

### Post by jacob.david on 2011-10-19
Usually while installing ubuntu it would have presented you with some options ( for e.g. to keep windows and install ubuntu side by side) and I'm not sure which one you chose. I hope you haven't overwritten your windows. Anyway can you boot into Ubuntu and execute 
sudo update-grub
and see whether it detects Windows 7.

---

### Post by garvinrick4 on 2011-10-19
> see whether it detects Windows 7.Already detects is in as a boot menu entry means os-prober has found it as an operating system.

---

### Post by lianazaman on 2011-10-19
> **garvinrick4 said:**
> If you want to know all about what is going on with your drive and what is there and not there and why
no boot do this below and post results so we can fix you up.
From Ubuntu download the bootscript from link
below to DESKTOP. Right click on and choose to extract with Archive Manager.
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/") 

Then run this line of code in terminal. [ctrl/alt/t]  (copy and paste it in to terminal hit enter)
     

     ```
sudo bash ~/Desktop/boot_info_script.sh
```Will make a RESULTS.txt file on Desktop open and copy and paste in a Message box and highlight
whole thing (is Long) and hit # in upper right of message box and will put in nice little box to read from.

Well, this is the results:
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for ?? on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 423639480 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for ?? on this drive. No errors found in the Boot 
                       Parameter Block.
sdb: ___________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc: ___________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   According to the info in the boot sector, sdc starts 
                       at sector 1. But according to the info from fdisk, sdc 
                       starts at sector 0.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   164,489,534   164,282,687   7 NTFS / exFAT / HPFS
/dev/sda3         164,489,596   488,396,799   323,907,204   f W95 Extended (LBA)
/dev/sda5         164,489,598   321,460,649   156,971,052   7 NTFS / exFAT / HPFS
/dev/sda6         484,734,976   488,396,799     3,661,824  82 Linux swap / Solaris
/dev/sda7         321,462,272   484,728,831   163,266,560  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        0EC029E7C029D62D                       ntfs       System Reserved
/dev/sda2        38623472623436CA                       ntfs       
/dev/sda5        01CC3CEA9E0B3450                       ntfs       Others
/dev/sda6        455920d5-9f08-4d59-a7fd-210c06d2f055   swap       
/dev/sda7        aedcce5b-c065-4c51-870f-f48fcefd4272   ext4       
/dev/sdb         32EF-88D0                              vfat       BLUECARNONA
/dev/sdc         3B21-0000                              vfat       BLUEBERNONA

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /tmp/BootInfo0/sda1      fuseblk    (ro,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5        /media/Others            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda7        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb         /media/BLUECARNONA       vfat       (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
/dev/sdc         /media/BLUEBERNONA       vfat       (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
/dev/sr0         /media/Ubuntu 11.10 i386 iso9660    (ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500,uhelper=udisks)


========================== sda1/grldr embedded menu: ===========================

--------------------------------------------------------------------------------

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdc

00000000  eb 58 90 46 69 6c 65 53  79 73 20 00 02 01 01 00  |.X.FileSys .....|
00000010  01 80 00 ae 01 f8 02 00  01 00 04 00 01 00 00 00  |................|
00000020  ae 01 00 00 80 00 29 00  00 21 3b 4e 4f 20 4e 41  |......)..!;NO NA|
00000030  4d 45 20 20 20 20 46 41  54 31 32 20 20 20 00 00  |ME    FAT12   ..|
00000040  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000050  00 00 00 00 00 00 00 00  00 00 fa b8 c0 07 8e d8  |................|
00000060  8e d0 bc 00 04 fb be 83  00 e8 0c 00 cd 18 f4 eb  |................|
00000070  fd b4 0e 33 db cd 10 c3  ac 0a c0 74 05 e8 f1 ff  |...3.......t....|
00000080  eb f6 c3 46 69 6c 65 20  53 79 73 74 65 6d 20 42  |...File System B|
00000090  6f 6f 74 20 53 65 63 74  6f 72 20 28 43 29 20 69  |oot Sector (C) i|
000000a0  73 20 72 65 73 65 72 76  65 64 2e 0a 0d 54 68 65  |s reserved...The|
000000b0  72 65 20 69 73 20 6e 6f  20 4f 53 20 74 6f 20 62  |re is no OS to b|
000000c0  6f 6f 74 20 6f 6e 20 74  68 69 73 20 64 69 73 6b  |oot on this disk|
000000d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

/home/lianazaman/Desktop/boot_info_script.sh: line 1888: (  / 2 ) + 16 : syntax error: operand expected (error token is "/ 2 ) + 16 ")
oks for, install "unlzma".
```> Usually while installing ubuntu it would have presented you with some  options ( for e.g. to keep windows and install ubuntu side by side) and  I'm not sure which one you chose. I hope you haven't overwritten your  windows. Anyway can you boot into Ubuntu and execute 
sudo update-grub
and see whether it detects Windows 7.     I got this...I think they can detect my Windows 7...
```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.0.0-12-generic
Found initrd image: /boot/initrd.img-3.0.0-12-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
```

---

### Post by jwbrase on 2011-10-19
> **lianazaman said:**
> Hi,

Been trying Ubuntu 11.10, and it's awesome (if not that there are some schoolwork I need to do with Windows). I tried to boot into Windows 7, but each time I choose Windows 7, it re-boot back to the choices. Means I can only enter Ubuntu, but not Windows 7, even if I choose that in the menu.

I'm not sure, but I think it's because I installed the bootloader options on the Windows 7 partition ( I thought if I do that, that means by default it will boot into Windows 7 if no choice was made. I was wrong.)

That's exactly it. Windows won't boot directly from GRUB, so GRUB has to call Windows' bootloader and have it boot Windows.

You wrote GRUB over the Windows bootloader, and told GRUB where Windows' bootloader had been before you overwrote it. Thus, when you try to boot Windows, GRUB calls itself.

I've made the same mistake, though under different circumstances (I simply wasn't paying attention to what I was doing).

> 
At first I thought of straight using Repair Disc Image (Windows), but that is usually been used when uninstalling Ubuntu to resolve the startup problem after uninstalling. I still want to use my Ubuntu though.

Any other alternative?

There should be an option on the Windows installation or recovery disk somewhere to restore your master boot record. I did it on an XP system, and it's been a few years, so I don't remember the details (and they may be different for Win7).

This will overwrite Grub (or, at least, the first stage of it), so you'll then need to use an Ubuntu LiveCD to reinstall Grub (putting it somewhere else this time). Once again, my memory is fuzzy, and, in addition, what exactly you want to do will depend on your setup (one hard disk or two, and how your disk(s) is/are partitioned).

---

### Post by lianazaman on 2011-10-19
> **jwbrase said:**
> That's exactly it. Windows won't boot directly from GRUB, so GRUB has to call Windows' bootloader and have it boot Windows.

You wrote GRUB over the Windows bootloader, and told GRUB where Windows' bootloader had been before you overwrote it. Thus, when you try to boot Windows, GRUB calls itself.

I've made the same mistake, though under different circumstances (I simply wasn't paying attention to what I was doing).



There should be an option on the Windows installation or recovery disk somewhere to restore your master boot record. I did it on an XP system, and it's been a few years, so I don't remember the details (and they may be different for Win7).

This will overwrite Grub (or, at least, the first stage of it), so you'll then need to use an Ubuntu LiveCD to reinstall Grub (putting it somewhere else this time). Once again, my memory is fuzzy, and, in addition, what exactly you want to do will depend on your setup (one hard disk or two, and how your disk(s) is/are partitioned).

Oh...Ahahah, just my luck, I guess I need to get back the cd from my bro ( gave it with my games, it's in one cd pack altogether XD ).

Still, any clue on how I make Windows 7 the default choice?

And how to reinstalle the Grub using the LiveCD? I mean should I put in codes int he terminal or something? So far I've only encountered the installation procedure, I haven't see anything else.

---

### Post by garvinrick4 on 2011-10-19
There are a few things to check:
Mount sda1 (System) in a live cd and see if there is a file named /boot and a file named /Boot. The one named
/Boot is the windows one make sure inside it has a BCD file that is the one you want.
rename the one named /boot or get rid of.   That should be the file you mistakenly put in sda1 from Ubuntu.
Then while you are in  the live cd. (Do not throw the one away with BCD inside of it that is windows) ( windows cannot differentiate between /boot and /Boot it is not case sensitive like Linux.)
```
sudo mount /dev/sda7 /mnt
``````
sudo grub-install --root-directory=/mnt /dev/sda
``````
sudo umount /mnt
``````
sudo reboot
```Hopefully all is well now.

## For some reason all of your bootscript is not there it does not show the part where what boot files
are where and what operating systems are in partitions but above is most likely right for what it looks like.


####Below is what you did and fix by instruction if you want to know.

Grub2 was installed with Windows system partition chosen as the root-directory. 
This causes the folder /boot/grub to be created on the Windows system partition. 
Since ntfs partitions are case insensitive this leads to confusions between "/boot" and the already existing folder "/Boot

Solution 
Boot into your Linux OS and deleted or rename the folder /boot on the Windows system partition. 
Make sure that your don't delete the /Boot folder. The /Boot folder contains the file "bcd" which is necessary to boot Windows Vista/7.

---

### Post by lianazaman on 2011-10-19
Erm...I checked in the FIle System (Windows), there is no boot folder, but there is a Boot folder.

---

### Post by garvinrick4 on 2011-10-19
Not in file system windows, in System partition which is first partition sda1 which is a Windows boot partition, shows /boot files in it in your
boot script. Windows is in second partition sda2.

sda1: 
 File system:       ntfs     Boot sector type:  Grub2 (v1.99)     Boot sector info: 
  [COLOR=Red]Grub2 (v1.99) is installed in the boot sector of sda1 [/COLOR](these are Ubuntu grub files should not be there) (should be in sda not sda1) (you have them in both sda and sda1) Remove from sda1. /boot
                        and looks at sector 423639480 of the same hard drive                         for core.img. core.img is at this location and looks                         for ?? on this drive. 
No errors found in the Boot                         Parameter Block. sdb: ___________________________________________

---

### Post by garvinrick4 on 2011-10-19
Here it is in Nautilus.

---

### Post by lianazaman on 2011-10-19
Ah...my mistake (again).

Can you tell me how to access the System partition or how to mount the System partition?

At first I thought searching through the system folder, and since I couldn't find any boot folder, I continued with the sudo code and I got:

```
File not found.
grub rescue>
```

---

### Post by garvinrick4 on 2011-10-19
> Can you tell me how to access the [COLOR=Red]System[/COLOR] partition or how to mount the System partition? Double click on it on left side of nautilus window. Click on screenshot I gave you.
If cannot find it:
sudo mkdir /media/system
sudo mount /dev/sda1 /media/system

Is it now on desktop.
Do not throw away /Boot folder with BCM in it but throw away /boot folder.

---

### Post by lianazaman on 2011-10-19
Agagagaga...in the end this is my solution:

1) Make sure you have backup for Ubuntu, and system image and restore for Windows. Both in an external device(Good thing I made it a habit, seeing as I always 'damage' things XD )

2) Insert System Image Repair disc. Restore to latest system image.

    -As my backup is for Windows only BEFORE installation of Ubuntu, it means I need to re-install Ubuntu.

3) Reinstall Ubuntu, then restore Backup..

A lot of work, but it seems my damaging hands, the more code I tried, the more worse it got. ^_^; . I pity my laptop, now he deserve a rest....

However, thanks you all for giving replies :)

p/s: I also found out we can make Windows 7 the default OS to boot using startup manager. ^_^ This forum really helps, and you guys did without even getting paid, that's truly sincere! <3 ya all!:D

---

