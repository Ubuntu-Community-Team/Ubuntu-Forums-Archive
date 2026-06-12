---
title: "Cannot boot, busybox (initramfs) error on boot"
date: 2011-06-19
forum: General Help
---

### Post by FLCL on 2011-06-19
When I try to boot I get a busybox error with (initramfs), booted to live CD to try and reinstall grub like mentioned in some other posts that said fixed the issue and I cannot mount my hard drive, it hangs. Just sits there doing nothing, not mounting, not giving an error, just sits there like it's processing.

Tried to check the disk and it tells me the hard drive is busy?

Also note I ran gparted and it said the hard drive was unmounted and even tried doing a check inside there and it said it was busy. Any ideas, the OS seems to think it's still active when it isn't

---

### Post by vivek.pandey on 2011-06-19
you can first try unmounting the disk manually before checking the disk....

---

### Post by FLCL on 2011-06-23
It's not mounted to begin with, or so it says...I'm on the live disc, and umount says ```
umount: /dev/sda1 is not mounted (according to mtab)

```

I tried fsck and it says:

```
ubuntu@ubuntu:~$ sudo fsck /dev/sda1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
fsck.ext4: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?

```

Also just want to add that when I try to **mount** the drive it goes down a line and then sits there with a blinking cursor doing nothing. Trying to mount through places does nothing( or the same thing just behind the scenes)

---

### Post by wildmanne39 on 2011-06-23
> **FLCL said:**
> When I try to boot I get a busybox error with (initramfs), booted to live CD to try and reinstall grub like mentioned in some other posts that said fixed the issue and I cannot mount my hard drive, it hangs. Just sits there doing nothing, not mounting, not giving an error, just sits there like it's processing.

Tried to check the disk and it tells me the hard drive is busy?

Also note I ran gparted and it said the hard drive was unmounted and even tried doing a check inside there and it said it was busy. Any ideas, the OS seems to think it's still active when it isn'tHi, you have to mount your partition with chroot, but first lets have a look at your disks.
post the information from this script so we can see where everything is located:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans

Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by FLCL on 2011-06-23
Here are the results:

>                   Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98 ) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for (,msdos1)/boot/grub.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   300,292,095   300,290,048  83 Linux
/dev/sda2         300,294,142   312,580,095    12,285,954   5 Extended
/dev/sda5         300,294,144   312,580,095    12,285,952  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        d2ef76e3-2df7-4c74-9402-d259fd419d80   ext4       
/dev/sda5        5203aaa2-a9b7-4d49-a84e-d743ba753a91   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /mnt                     unknown    (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  8b c6 8d 65 e0 5f 5e 5b  8b 4d fc 33 cd e8 5b 8d  |...e._^[.M.3..[.|
00000010  ff ff c9 c3 55 8b ec 83  ec 10 ff 75 08 8d 4d f0  |....U......u..M.|
00000020  e8 c0 92 ff ff ff 75 28  8d 4d f0 ff 75 24 ff 75  |......u(.M..u$.u|
00000030  20 ff 75 1c ff 75 18 ff  75 14 ff 75 10 ff 75 0c  | .u..u..u..u..u.|
00000040  e8 2d fc ff ff 83 c4 20  80 7d fc 00 74 07 8b 4d  |.-..... .}..t..M|
00000050  f8 83 61 70 fd c9 c3 55  8b ec 51 51 a1 48 00 41  |..ap...U..QQ.H.A|
00000060  00 33 c5 89 45 fc a1 50  29 41 00 53 56 33 db 3b  |.3..E..P)A.SV3.;|
00000070  c3 57 8b f9 75 3a 8d 45  f8 50 33 f6 46 56 68 7c  |.W..u:.E.P3.FVh||
00000080  25 40 00 56 ff 15 68 10  40 00 85 c0 74 08 89 35  |%@.V..h.@...t..5|
00000090  50 29 41 00 eb 34 ff 15  34 10 40 00 83 f8 78 75  |P)A..4..4.@...xu|
000000a0  0a 6a 02 58 a3 50 29 41  00 eb 05 a1 50 29 41 00  |.j.X.P)A....P)A.|
000000b0  83 f8 02 0f 84 cf 00 00  00 3b c3 0f 84 c7 00 00  |.........;......|
000000c0  00 83 f8 01 0f 85 e8 00  00 00 39 5d 18 89 5d f8  |..........9]..].|
000000d0  75 08 8b 07 8b 40 04 89  45 18 8b 35 a4 10 40 00  |u....@..E..5..@.|
000000e0  33 c0 39 5d 20 53 53 ff  75 10 0f 95 c0 ff 75 0c  |3.9] SS.u.....u.|
000000f0  8d 04 c5 01 00 00 00 50  ff 75 18 ff d6 8b f8 3b  |.......P.u.....;|
00000100  fb 0f 84 ab 00 00 00 7e  3c 81 ff f0 ff ff 7f 77  |.......~<......w|
00000110  34 8d 44 3f 08 3d 00 04  00 00 77 13 e8 4f 09 00  |4.D?.=....w..O..|
00000120  00 8b c4 3b c3 74 1c c7  00 cc cc 00 00 eb 11 50  |...;.t.........P|
00000130  e8 4a e5 ff ff 3b c3 59  74 09 c7 00 dd dd 00 00  |.J...;.Yt.......|
00000140  83 c0 08 8b d8 85 db 74  69 8d 04 3f 50 6a 00 53  |.......ti..?Pj.S|
00000150  e8 1b 8d ff ff 83 c4 0c  57 53 ff 75 10 ff 75 0c  |........WS.u..u.|
00000160  6a 01 ff 75 18 ff d6 85  c0 74 11 ff 75 14 50 53  |j..u.....t..u.PS|
00000170  ff 75 08 ff 15 68 10 40  00 89 45 f8 53 e8 74 d0  |.u...h.@..E.S.t.|
00000180  ff ff 8b 45 f8 59 eb 75  33 f6 39 5d 1c 75 08 8b  |...E.Y.u3.9].u..|
00000190  07 8b 40 14 89 45 1c 39  5d 18 75 08 8b 07 8b 40  |..@..E.9].u....@|
000001a0  04 89 45 18 ff 75 1c e8  be 06 00 00 83 f8 ff 59  |..E..u.........Y|
000001b0  75 04 33 c0 eb 47 3b 45  18 74 1e 53 53 8d 00 fe  |u.3..G;E.t.SS...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 78 bb 00 00 00  |...........x....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200




I also left for a while after I tried mounting and came back to this error:

```
**Unable to mount 154 GB Filesystem**
DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

```

---

### Post by wildmanne39 on 2011-06-23
Hi, did you post everything the script said? if so you have a partition problem. Run this command from terminal while using the livcd.
```
sudo e2fsck -C -0 -p -f -v /dev/sda
```Let me know what it says.

---

### Post by FLCL on 2011-06-23
Yeah thats everything that was in the results.txt, I just selected all and pasted it in the post.

Ran that command and it tells me it's busy. > ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda
e2fsck: Device or resource busy while trying to open /dev/sda
Filesystem mounted or opened exclusively by another program?


---

### Post by wildmanne39 on 2011-06-23
> **FLCL said:**
> Yeah thats everything that was in the results.txt, I just selected all and pasted it in the post.

Ran that command and it tells me it's busy.Hi, open disk utility in the livecd and unmount the drive and try that command again.

---

### Post by FLCL on 2011-06-23
It says it isn't mounted, also ran umount and it returns > ubuntu@ubuntu:~$ umount /dev/sda
umount: /dev/sda is not mounted (according to mtab)
 tried mounting in disk utility to see if I could unmount after and the wheel just spins forever trying to mount

---

### Post by wildmanne39 on 2011-06-23
> **FLCL said:**
> It says it isn't mounted, also ran umount and it returns 
 tried mounting in disk utility to see if I could unmount after and the wheel just spins forever trying to mountHi, I am going to give you a link for a program that will make it is to repair grub, if that is the only issue, but it looks like your file system is corrupted and you need to use testdisk to repair it, but try the link first.
[http://ubuntuforums.org/showthread.php?p=10871917#post10871917](http://ubuntuforums.org/showthread.php?p=10871917#post10871917)

---

### Post by FLCL on 2011-06-29
Sorry for the late response, haven't been able to get around to it. i've burned the CD and ran it live from the cd. When I tried using the boot-repair it starts and says it's scanning hardware and it may take a few seconds, but it's been doing that for about 30 minutes now and hasn't done anything else...could this be due to the fact that I can't mount the hard drive?

---

### Post by FLCL on 2011-07-01
bump

---

### Post by wildmanne39 on 2011-07-01
> **FLCL said:**
> Sorry for the late response, haven't been able to get around to it. i've burned the CD and ran it live from the cd. When I tried using the boot-repair it starts and says it's scanning hardware and it may take a few seconds, but it's been doing that for about 30 minutes now and hasn't done anything else...could this be due to the fact that I can't mount the hard drive?Hi, I think it is because you have a corrupt partition, I am going to give you a link so you can run testdisk on it it can recover partitions, but I have not used it myself.
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)

---

### Post by FLCL on 2011-07-04
Well i went ahead and ran it, it detected the partitions fine, after analyzing them i had it wrote the new partition table and rebooted but it's still jacked up. Cannot boot into the system, I think it's history, whatever the hell happened really did a number

---

### Post by wildmanne39 on 2011-07-04
> **FLCL said:**
> Well i went ahead and ran it, it detected the partitions fine, after analyzing them i had it wrote the new partition table and rebooted but it's still jacked up. Cannot boot into the system, I think it's history, whatever the hell happened really did a number
Hi, since you ran testdisk if you want you can run the boot script information again and post it here so we can see if it recovered your partitions if it did we might can reinstall grub now.

---

### Post by in-dust-rial on 2011-07-04
hi,
grub comes with a live console while in bootloader menue.
this means, if you are choosing the option to load, you can press a botton (i think 'e' for 'edit').
afterwards you can manipulate the grub entry.
more especially the 'root' line.

the console comes with a completion option.
so hit the tab key a lot. (enter 'root (h' and then TABTABTABTABTABTAB-crazy and options will be displayed')
just try to load ALL partitions. 
dont leave one out.
I experienced, that the device mapping was twisted. 
so what grub knew to be the root partition while install was now a different partition. so I had to find what name applied to the actual install.

...
also after having a running system again - you might want to use the 'dd' command to save the MBR into a file on a backup medium. then you can always restore the MBR after you f***** it up.

GOOD LUCK.

---

### Post by akutonpa on 2013-03-06
Thanks to the advice on the thread.

I had the busybox (initramfs) error on boot.

I booted from latest live CD on a flash drive. Selected try the latest ubuntu without installing. I selected Gparted from the system tools menu. From the GUI of Gparted I highlighted the partition ubuntu was on (for me sda1), right clicked on it, selected check from the drop down menu. Clicked the apply button. After the partition was checked, I rebooted the computer (flashdisk removed) and it booted up normally.

So a big thanks for the advice.

---

