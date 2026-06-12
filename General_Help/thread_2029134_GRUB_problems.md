---
title: "GRUB problems"
date: 2012-07-19
forum: General Help
---

### Post by Jonners59 on 2012-07-19
I have just installed 12:04 from LiveCD after having to do a rebuild.  I am now running in to problems.

First the HW:
1x 500G HD sda - this is new as I have just replaced the origional HD as it was showing errors.  This is the HD I run Ubuntu off of.
1 x 700G HD sdb - this is where files are stored
1x 1T HD sdc - Backup of the 700Gb HD and some files from the origional 500Gb HD
No video card, use the bult in

64b but only 3.8Gb RAM

Summary of actions:
To load the LiveCD I needed to F6 and change the settings to acpi=off and nomodeset
Otherwise it booted as normal

After install, when I rebooted the screen went blank selecting the OS in GRUB

Tried e and added nomodest to the end of the second to bottom line of the editor. = failed to start

Tried a purge and re-install cmd I found and now when it boots it loads in to a Grub terminal "GRUB>" and expects some code....

I tried installing Boot-repair and followed the simple repair it says all went well, but after reboot I have the same problem.  It goes in to the GRUB terminal

Any ideas how to fix this please....

---

### Post by drs305 on 2012-07-19
From the Boot Repair app please run the boot info script and either post the contents of RESULTS.txt or a link to it. The GRUB prompt probably means it's not finding the Grub menu file.

---

### Post by Jonners59 on 2012-07-19
I need to re install it as I have done a reboot..., but here is the output of the script manager I used a couple of years ago, whilst I re install... 

PS: many thanks :)

OK update - I have reinstalled and now done:
[URL: http://paste.ubuntu.com/1100465/]("url:%20http://paste.ubuntu.com/1100465/")




```
 Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/grub on this drive.
 => Lilo is installed in the MBR of /dev/sdb.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdc and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks for (UUID=b8d7b190-ab7b-48a2-a4f8-b3e9ff4e50bb)/boot/grub on this 
    drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /etc/fstab

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda11: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500106780160 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976771055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048     2,160,639     2,158,592  83 Linux
/dev/sda2    *      2,160,640    99,620,863    97,460,224  83 Linux
/dev/sda3          99,620,864   880,871,423   781,250,560  83 Linux
/dev/sda4         880,873,470   976,769,023    95,895,554   5 Extended
/dev/sda5         880,873,472   910,362,623    29,489,152  82 Linux swap / Solaris
/dev/sda6         910,364,672   929,896,447    19,531,776  83 Linux
/dev/sda7         929,898,496   951,377,919    21,479,424  83 Linux
/dev/sda8         951,379,968   961,144,831     9,764,864  83 Linux
/dev/sda9         961,146,880   967,004,159     5,857,280  83 Linux
/dev/sda10        967,006,208   972,863,487     5,857,280  83 Linux
/dev/sda11        972,865,536   976,769,023     3,903,488  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                   1   414,646,271   414,646,271   5 Extended
/dev/sdb5                  63   320,143,319   320,143,257  83 Linux
/dev/sdb2         414,646,272 1,953,523,711 1,538,877,440  83 Linux


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               2,048 1,465,147,391 1,465,145,344  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        3dbf4243-32c2-4fbe-9f14-58fb65702930   ext4       Boot
/dev/sda10       727321b9-6991-4450-bea9-afc481d0cc6f   ext4       OPT
/dev/sda11       73163ea5-d9bb-4010-ba6d-ae65329bf7b5   ext4       USRlocal
/dev/sda2        483f0e31-f129-4a95-97b2-ba8ab818c91a   ext4       ROOT
/dev/sda3        51ae9a68-4999-4bee-bb19-0859cd099edf   ext4       HOME
/dev/sda5        9702c022-c710-48e3-958d-f89b2b573305   swap       SWAP
/dev/sda6        e8ebe4de-6983-446f-ac44-34978274cedd   ext4       VAR
/dev/sda7        7632e5b4-3be6-4cb6-9c29-6124b30cf4e5   ext4       USR
/dev/sda8        f9680a74-898f-4915-8055-d0bce3ad31eb   ext4       TEMP
/dev/sda9        5b47e15b-814f-4fe0-8c86-37ab36bf54fa   ext4       srv
/dev/sdb2        4113d69b-894f-4aa5-9777-30968d7d1fef   ext4       Backup
/dev/sdb5        bca6a987-c63b-4e60-b1d8-4750201a9b69   ext4       Configs
/dev/sdc1        a4e24d6a-4a48-4908-8a86-daf751432fd7   ext4       Home

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda3        /media/HOME              ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdc1        /media/Home              ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


============================= sda1/grub/grub.cfg: ==============================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                grub/core.img                                  1
               =                grub/grub.cfg                                  1
               =                initrd.img-3.2.0-23-generic                    1
               =                vmlinuz-3.2.0-23-generic                       1

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=483f0e31-f129-4a95-97b2-ba8ab818c91a /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
#UUID=3dbf4243-32c2-4fbe-9f14-58fb65702930 /boot           ext4    defaults        0       2
# /home was on /dev/sda3 during installation
UUID=51ae9a68-4999-4bee-bb19-0859cd099edf /home           ext4    defaults        0       2
# /opt was on /dev/sda10 during installation
UUID=727321b9-6991-4450-bea9-afc481d0cc6f /opt            ext4    defaults        0       2
# /srv was on /dev/sda9 during installation
UUID=5b47e15b-814f-4fe0-8c86-37ab36bf54fa /srv            ext4    defaults        0       2
# /tmp was on /dev/sda8 during installation
UUID=f9680a74-898f-4915-8055-d0bce3ad31eb /tmp            ext4    defaults        0       2
# /usr was on /dev/sda6 during installation
#UUID=e8ebe4de-6983-446f-ac44-34978274cedd /usr            ext4    defaults        0       2
# /usr/local was on /dev/sda11 during installation
UUID=73163ea5-d9bb-4010-ba6d-ae65329bf7b5 /usr/local      ext4    defaults        0       2
# /var was on /dev/sda7 during installation
UUID=7632e5b4-3be6-4cb6-9c29-6124b30cf4e5 /var            ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=9702c022-c710-48e3-958d-f89b2b573305 none            swap    sw              0       0
UUID=3dbf4243-32c2-4fbe-9f14-58fb65702930    /boot    ext4    defaults    0    2
UUID=e8ebe4de-6983-446f-ac44-34978274cedd    /usr    ext4    defaults    0    2
--------------------------------------------------------------------------------

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  92 b9 90 24 87 c6 51 ed  02 d8 72 88 38 93 da 83  |...$..Q...r.8...|
00000010  0b 31 3e de 7a f7 d4 0e  f0 2c 47 eb e5 af 9c 91  |.1>.z....,G.....|
00000020  04 86 ea 81 99 0a 95 8e  b7 56 5b 2d f9 85 2c 5a  |.........V[-..,Z|
00000030  3a 9a 4b 43 cf 21 d3 d6  de 21 8c 3f a3 4e 92 13  |:.KC.!...!.?.N..|
00000040  09 8e 68 d3 9f 49 d6 0b  36 38 6d 8d 5a 89 81 3f  |..h..I..68m.Z..?|
00000050  b5 a5 f9 a3 06 6a 9a 0c  9f d3 b5 e7 e9 9f d1 50  |.....j.........P|
00000060  ac d1 17 43 40 44 38 e1  23 94 f8 5f e1 c5 94 2d  |...C@D8.#.._...-|
00000070  90 4c a1 aa dd cf 2d 95  1d 78 2c f2 71 0f 32 eb  |.L....-..x,.q.2.|
00000080  2a da 62 d3 b5 26 3f 4b  29 3a 28 1e 4e 2b 02 71  |*.b..&?K):(.N+.q|
00000090  6d d0 8e 58 5d 3f f7 99  4a 97 4b bd f8 7d 09 9e  |m..X]?..J.K..}..|
000000a0  88 3a 1b 2c 94 f5 c4 bd  b6 ff 09 3d 87 b7 de 79  |.:.,.......=...y|
000000b0  0e 96 89 eb 73 db d9 3f  1c 11 67 5a e6 e5 84 46  |....s..?..gZ...F|
000000c0  d6 e7 f4 b7 20 06 d4 23  32 09 40 a4 9c 89 48 06  |.... ..#2.@...H.|
000000d0  8e 14 61 9b 1b d6 4c 94  84 8b 73 fc e1 8a de a0  |..a...L...s.....|
000000e0  6c 55 48 1b 07 27 61 90  80 51 47 07 4a 6a 59 6a  |lUH..'a..QG.JjYj|
000000f0  1d 04 a9 6f ab 9a 8f c0  cd 6b 10 8c 06 97 72 24  |...o.....k....r$|
00000100  95 f3 f9 57 93 d3 f5 67  62 bc 56 e3 14 47 81 5c  |...W...gb.V..G.\|
00000110  26 be 43 cb b9 cb 6c 1d  43 8c 13 14 82 ed e2 78  |&.C...l.C......x|
00000120  9d 64 9c f1 b7 e2 88 57  87 0a 11 b9 6c 12 ee 31  |.d.....W....l..1|
00000130  34 ae fe 8b 99 48 32 d2  fc 1f fd 6e 32 8d 2b f5  |4....H2....n2.+.|
00000140  16 a9 59 61 67 12 b3 ff  45 20 d1 23 bd 85 e6 8b  |..Yag...E .#....|
00000150  0a b9 d4 5e d9 b1 31 ad  72 b3 65 cd d4 1a ee 4e  |...^..1.r.e....N|
00000160  1b b8 6b 2d 14 9e 17 26  b9 90 8d 7a 99 d7 51 05  |..k-...&...z..Q.|
00000170  a8 c6 6e 8d ef 18 6e 73  fb 80 ba 3f 89 29 36 b3  |..n...ns...?.)6.|
00000180  86 18 a6 2f bf ee be 0d  53 a8 65 50 45 90 a8 a6  |.../....S.ePE...|
00000190  39 d2 69 60 fa b5 00 cb  47 5c f4 ff bb 3a c8 9f  |9.i`....G\...:..|
000001a0  42 a5 68 5a 83 e0 8b c6  04 22 21 11 5d 73 15 16  |B.hZ....."!.]s..|
000001b0  72 88 e5 66 a1 26 d5 5d  70 08 d5 74 b9 37 00 fe  |r..f.&.]p..t.7..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 f8 c1 01 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 f8  c1 01 00 10 2a 01 00 00  |............*...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

```

---

### Post by drs305 on 2012-07-19
Try running Boot Repair again, making sure you tick the box indicating you have a separate /boot partition - it's under Advanced  > Grub Location.   A valid grub.cfg file doesn't exist, but if you indicate where the /boot files are Boot Repair may be able to fix things. If not, post the script results.

---

### Post by darkod on 2012-07-19
Have you tried this:
1. Boot with the 12.04 cd in live mode (add any parameters that you need to do this).
2. Open /dev/sda1 and delete the /boot/grub/core.img file/folder.
3. Then open terminal and try:
```
sudo mount /dev/sda2 /mnt
sudo mount /dev/sda1 /mnt/boot
sudo grub-install --boot-directory=/mnt/boot /dev/sda
```

Restart and make sure /dev/sda is the first disk you are booting from (the 500GB disk).

If that doesn't work, try again only now modify the third command to be:
```
sudo grub-install --root-directory=/mnt /dev/sda
```

Let us know what happens.

---

### Post by Jonners59 on 2012-07-19
> **darkod said:**
> Have you tried this:
1. Boot with the 12.04 cd in live mode (add any parameters that you need to do this).
2. Open /dev/sda1 and delete the /boot/grub/core.img file/folder.
3. Then open terminal and try:
```
sudo mount /dev/sda2 /mnt
sudo mount /dev/sda1 /mnt/boot
sudo grub-install --boot-directory=/mnt/boot /dev/sda
```Restart and make sure /dev/sda is the first disk you are booting from (the 500GB disk).

If that doesn't work, try again only now modify the third command to be:
```
sudo grub-install --root-directory=/mnt /dev/sda
```
Let us know what happens.

OK, just tried these and it did not work....  Both failed.
[HTML]ubuntu@ubuntu:~$ sudo chown root /media/Boot/boot/grub/core.img
ubuntu@ubuntu:~$ sudo chmod 777 /media/Boot/boot/grub/core.img
ubuntu@ubuntu:~$ sudo rm /media/Boot/boot/grub/core.img
ubuntu@ubuntu:~$ sudo mount /dev/sda2 /mnt
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/boot
ubuntu@ubuntu:~$ sudo grub-install --boot-directory=/mnt/boot /dev/sda
Installation finished. No error reported.[/HTML]

---

### Post by darkod on 2012-07-19
There is a grub.cfg on sda1 but it doesn't seem to pick it up. Try purging and reinstalling grub2 from live mode:
```
sudo mount /dev/sda2 /mnt
sudo mount /dev/sda1 /mnt/boot
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
```

Purge and reinstall grub2 and recreate the config files:
```
apt-get remove --purge grub-pc grub-common
apt-get install grub-pc
grub-mkconfig
update-grub
grub-install /dev/sda
```

Exit chroot and unmount all:
```
exit
sudo umount /mnt/sys
sudo umount /mnt/proc
sudo umount /mnt/dev
sudo umount /mnt/boot
sudo umount /mnt
```

Restart and see if that helps. It should, if the installation is OK in the first place.

---

### Post by Jonners59 on 2012-07-19
OK
I just tried 
> **drs305 said:**
> Try running Boot Repair again, making sure you  tick the box indicating you have a separate /boot partition - it's under  Advanced  > Grub Location.   A valid grub.cfg file doesn't exist,  but if you indicate where the /boot files are Boot Repair may be able to  fix things. If not, post the script results.

And just booting up again.  Am going to try again, but just checking that sda1 is boot, I noticed in the log sda2 was boot....

I'll then try your new suggestion.  Must also drop mum off in between!  bless :)

---

### Post by darkod on 2012-07-19
> **Jonners59 said:**
> OK
I just tried 


And just booting up again.  Am going to try again, but just checking that sda1 is boot, I noticed in the log sda2 was boot....

I'll then try your new suggestion.  Must also drop mum off in between!  bless :)

What do you mean sda2 was boot?

If you mean the boot flag, don't bother with it. You can leave it on sda2 since linux doesn't use it.

Otherwise, in ubuntu, sda1 is (was) your /boot partition, and sda2 is the / partition.

---

### Post by Jonners59 on 2012-07-19
> **darkod said:**
> What do you mean sda2 was boot?

If you mean the boot flag, don't bother with it. You can leave it on sda2 since linux doesn't use it.

Otherwise, in ubuntu, sda1 is (was) your /boot partition, and sda2 is the / partition.

Well that explains why it made no difference :lol:

Am trying your suggestions below... ANd I just realised, I should check the boot order on the motherboard BIOS setting in case it had changed.  I noticed something in the log that said there was some sort of GRUB in sdc.....  Worth checking in case it had changed.

Feed back in a minute
[http://paste.ubuntu.com/1100785]("url:%20http://paste.ubuntu.com/1100465/")

---

### Post by darkod on 2012-07-19
> **Jonners59 said:**
> Well that explains why it made no difference :lol:

Am trying your suggestions below... ANd I just realised, I should check the boot order on the motherboard BIOS setting in case it had changed.  I noticed something in the log that said there was some sort of GRUB in sdc.....  Worth checking in case it had changed.

Feed back in a minute
[http://paste.ubuntu.com/1100785]("url:%20http://paste.ubuntu.com/1100465/")

Well, I did mention in the first post to make sure you are booting from the /dev/sda disk. That's the 500GB disk.

Otherwise it's pointless reinstalling grub2 to it, if you are not even booting from it. :)

---

### Post by Jonners59 on 2012-07-19
I'm in the midst of doin the install cmds you listed, but I am stuck

I have done the remove and purge, and now doing the install, but it asks me which drive to install in, I can not select any.  It has a red "block" in the tick box.  I have tried everything to make a selection, but as soon as I select "OK" my selection disappears and the next screen it says I did not select a HD to install to.....

How do I select or is this not important?????

---

### Post by darkod on 2012-07-19
I don't think any windows should come up, but in case it does, in the windows made in text mode you select with Space once the correct square is selected. It would usually put X when it's marked.

Only then do the OK.

---

### Post by Jonners59 on 2012-07-19
The only character I did not try  Ggrrrrrrr

OK, so i selected the correct device, sda, but it says it failed to insall to dev/sda

What next.  It is going in a loop

Also the ```
sudo chroot /mnt
``` that too was not recognised or at least it said 

```
Groups:  Command not found
``` .:confused:

---

### Post by oldfred on 2012-07-19
I have never chrooted a system with every folder in a separate partition. Not sure if some of them also need to be mounted.

But your fstab has the/boot entry commented out. Were you trying to move /boot back into / (root).

Next time you install:
For standard desktops you do not need each system folder in a separate partition. That was for servers and only where the owner knew when certain tasks need separation. 

Default install by Ubuntu is just / (root) and swap. Herman does not even use swap.

Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

---

### Post by darkod on 2012-07-19
> **Jonners59 said:**
> The only character I did not try  Ggrrrrrrr

OK, so i selected the correct device, sda, but it says it failed to insall to dev/sda

What next.  It is going in a loop

Also the ```
sudo chroot /mnt
``` that too was not recognised.:confused:

Well, that is a problem. If any command fails, especially from the first group of commands, don't continue because it's pointless.

The chroot should work if all commands above have been executed correctly. And if you start from live mode, which means no hdd partitions should be mounted. You didn't mount anything before you started right?

Try it again.

---

### Post by darkod on 2012-07-19
oldfred, /boot is commented out at the top, the default entry, but towards the botoom of fstab there is another entry with the correct UUID mounted as /boot.

oldfred might have a point, you might need to mount more partitions after mounting sda1 as /mnt/boot in the first group of commands. You have split it too much, not sure if there is any reason for that.

You can follow the fstab and if it says sda6 was /usr at install for example, just do:
sudo mount /dev/sda6 /mnt/usr

Do that for all partitions to make sure the chroot will work.

---

### Post by Jonners59 on 2012-07-19
> **oldfred said:**
> 
But your fstab has the/boot entry commented out. Were you trying to move /boot back into / (root).


No, not touched it.  Just trying to get it started.  It worked fine for months as do all the other machines in this config for years.  This one failed after an update in Update Manager which screwed my Virtual Machine, which was the isolated to a prob in dkms and dopmod (or whatever it was)...  No one knew how to fix, so I decided it was quicker and easier to do a rebuild.  The build is done, but it won't boot.

I'll do another rebuild!!!  Sadly i think I'll get stuck at the same point, but at least I'll be over this hurdle.  I still think it has something to do with the sdc GRUB found in the log, but it is only a gut feel.  I would like to find it and remove it.

---

### Post by Jonners59 on 2012-07-19
> **darkod said:**
> oldfred, /boot is commented out at the top, the default entry, but towards the botoom of fstab there is another entry with the correct uuid mounted as /boot.

Oldfred might have a point, you might need to mount more partitions after mounting sda1 as /mnt/boot in the first group of commands. You have split it too much, not sure if there is any reason for that.

You can follow the fstab and if it says sda6 was /usr at install for example, just do:
Sudo mount /dev/sda6 /mnt/usr

do that for all partitions to make sure the chroot will work.

ok

---

### Post by Jonners59 on 2012-07-19
No going for rebuild again....

---

### Post by darkod on 2012-07-19
If by rebuild you mean reinstall, this might be a chance to delete all those partitions and do a more compact install. Again, unless there is a real good reason having the installation split so much.

Having separate /boot is not a problem, especially if your BIOS has the 137GB limit problem, and separate /home is worth having too. But having all those separate partitions looks too much.

---

### Post by Jonners59 on 2012-07-19
Gone for a simpler build. root, home, swap.......  Should be done by morning.

OK, all is working again and almost setup.  To make it work I disconnected the sdc drive, this removed any ambiguity over GRUB installs.  I used GRUB-Customizer to config the GRUB including the "nomodeset and apic=off, which is very easy and works in this app...  I have not heard anyone have any luck with Boot-Repair though the log is useful.  I have installed both.....

Now to complete my restore and the thing that caused all the probs - VIRTUAL BOX

Thank you all for your kind help and staying up with me past mid night last night.

---

