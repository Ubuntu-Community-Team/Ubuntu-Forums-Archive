---
title: "Ubuntu would not boot after Windows repartitioning the HDD"
date: 2011-12-07
forum: General Help
---

### Post by hariks0 on 2011-12-07
I hope the title says it all. I had merged, deleted and created some partitions from Windows Disk Management tool. The Ubuntu bootsplash just hangs when booting. Nothing appears even if F1, F2 to F7 are pressed.

TIA

---

### Post by BC59 on 2011-12-07
> **hariks0 said:**
> I hope the title says it all. I had merged, deleted and created some partitions from Windows Disk Management tool. The Ubuntu bootsplash just hangs when booting. Nothing appears even if F1, F2 to F7 are pressed.

TIA

Why don't you try Boot Repair?

---

### Post by coffeecat on 2011-12-07
@hariks0, we need to see what state your partitions are in now after being rearranged with the Windows Disk Management Utility, as well as other details of your system.

Boot up the live Ubuntu CD, choose 'try Ubuntu' to get to the live desktop, ensure you are connected to the internet, and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script - the instructions are on that page - and post the contents of the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags for clarity. The simplest way of doing this is to highlight the output and then click on the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the message toolbar.

---

### Post by hariks0 on 2011-12-08
/etc/fstab contents
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda11 during installation
UUID=18c3d505-a291-4cbd-a513-a3580d94b7d5 /               ext4    errors=remount-ro 0       1
# /C was on /dev/sda2 during installation
UUID=D020576520575198 /C              ntfs    defaults,umask=007,gid=46 0       0
# /D was on /dev/sda5 during installation
UUID=4024497624497048 /D              ntfs    defaults,umask=007,gid=46 0       0
# /E was on /dev/sda6 during installation
/dev/sdb13 /E              ntfs    defaults,umask=007,gid=46 0       0
# /F was on /dev/sda7 during installation
UUID=03AB01E67E33EB5F /F              ntfs    defaults,umask=007,gid=46 0       0
# /G was on /dev/sda8 during installation
UUID=3B87373743B2E5BD /G              ntfs    defaults,umask=007,gid=46 0       0
# /H was on /dev/sda9 during installation
UUID=174AC7022D706F8D /H              ntfs    defaults,umask=007,gid=46 0       0
# /I was on /dev/sda13 during installation
UUID=6a1d65d8-0234-47a1-9497-a0884f55eaa7 /I              ext4    defaults        0       2
# /home was on /dev/sda12 during installation
UUID=35e79e92-d41d-4f98-a40f-8401c35aecf8 /home           ext4    defaults        0       2
# swap was on /dev/sda10 during installation
UUID=e01f4747-b327-4a5e-8983-303a54ddf7c8 none            swap    sw              0       0
```
Fdisk output :
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
191 heads, 63 sectors/track, 40588 cylinders
Units = cylinders of 12033 * 512 = 6160896 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6e629b6d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8510    51197952    7  HPFS/NTFS
/dev/sda2            8510       40588   192998190+   f  W95 Ext'd (LBA)
/dev/sda5            8510       17020    51199123+   7  HPFS/NTFS
/dev/sda6           17020       22125    30716248+   7  HPFS/NTFS
/dev/sda7           22125       30376    49640818+   7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4be646c2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2              13        6374    51094727    7  HPFS/NTFS
/dev/sdb3            6375      121601   925560877+   f  W95 Ext'd (LBA)
/dev/sdb5            6375       16572    81915403+   7  HPFS/NTFS
/dev/sdb6           16573       31263   118000000    7  HPFS/NTFS
/dev/sdb7           31263       43428    97717248    7  HPFS/NTFS
/dev/sdb8           43428       60814   139646976    7  HPFS/NTFS
/dev/sdb9           60814       61421     4881408   82  Linux swap / Solaris
/dev/sdb10          61422       64461    24413184   83  Linux
/dev/sdb11          64461       72971    68358144   83  Linux
/dev/sdb12          72971       91208   146484224   83  Linux
/dev/sdb13          91209      121601   244131741    7  HPFS/NTFS
ubuntu@ubuntu:~$ 
```
Terminal output:
```
ubuntu@ubuntu:~$ sudo bash '/home/ubuntu/Downloads/boot_info_script.sh' 

boot_info_script version: 0.60        [17 May 2011]


[COLOR="Red"]"gawk" could not be found, using "busybox awk" instead.
This may lead to unreliable results.[/COLOR]

Identifying MBRs...
Computing Partition Table of /dev/sda...
Computing Partition Table of /dev/sdb...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda5 for information... 
Searching sda6 for information... 
Searching sda7 for information... 
Searching sdb1 for information... 

Finished. The results are in the file "RESULTS.txt"
located in "/home/ubuntu/Downloads/".

ubuntu@ubuntu:~$
```

Script Result:
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 10 for /boot/burg.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 2. But according to the info from fdisk, 
                       sda5 starts at sector 102398373.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
191 heads, 63 sectors/track, 40588 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   102,397,951   102,395,904   7 NTFS / exFAT / HPFS
/dev/sda2         102,398,371   488,394,751   385,996,381   f W95 Extended (LBA)
/dev/sda5         102,398,373   204,796,619   102,398,247   7 NTFS / exFAT / HPFS
/dev/sda6         204,796,683   266,229,179    61,432,497   7 NTFS / exFAT / HPFS
/dev/sda7         266,229,243   365,510,879    99,281,637   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sdb2             206,848   102,396,301   102,189,454   7 NTFS / exFAT / HPFS
/dev/sdb3         102,398,310 1,953,520,064 1,851,121,755   f W95 Extended (LBA)
/dev/sdb5         102,398,373   266,229,179   163,830,807   7 NTFS / exFAT / HPFS
/dev/sdb6         266,229,243   502,229,242   236,000,000   7 NTFS / exFAT / HPFS
/dev/sdb7         502,231,040   697,665,535   195,434,496   7 NTFS / exFAT / HPFS
/dev/sdb8         697,667,584   976,961,535   279,293,952   7 NTFS / exFAT / HPFS
/dev/sdb9         976,963,584   986,726,399     9,762,816  82 Linux swap / Solaris
/dev/sdb10        986,728,448 1,035,554,815    48,826,368  83 Linux
/dev/sdb11      1,035,556,864 1,172,273,151   136,716,288  83 Linux
/dev/sdb12      1,172,275,200 1,465,243,647   292,968,448  83 Linux
/dev/sdb13      1,465,256,583 1,953,520,064   488,263,482   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        36C6A6E5C6A6A499                       ntfs       
/dev/sda5        68907E1C907DF0C4                       ntfs       DDrive
/dev/sda6        46400AAF400AA631                       ntfs       EDrive
/dev/sda7        03AB01E67E33EB5F                       ntfs       MM
/dev/sdb1        D0B04EA5B04E91C0                       ntfs       System Reserved
/dev/sdb10       18c3d505-a291-4cbd-a513-a3580d94b7d5   ext4       
/dev/sdb11       35e79e92-d41d-4f98-a40f-8401c35aecf8   ext4       
/dev/sdb12       6a1d65d8-0234-47a1-9497-a0884f55eaa7   ext4       
/dev/sdb13       01CC6C1A27B00BA0                       ntfs       Videos
/dev/sdb2        D020576520575198                       ntfs       
/dev/sdb5        4024497624497048                       ntfs       DDrive
/dev/sdb6        03AB01E67E33EB5F                       ntfs       Audio
/dev/sdb7        3B87373743B2E5BD                       ntfs       ISO
/dev/sdb8        F0067F2A067EF148                       ntfs       Images
/dev/sdb9        e01f4747-b327-4a5e-8983-303a54ddf7c8   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /tmp/BootInfo0/sdb1      fuseblk    (ro,nosuid,nodev,allow_other,blksize=4096)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


========================== sdb1/grldr embedded menu: ===========================

--------------------------------------------------------------------------------

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  ab 02 95 cf 2f 2f ff fb  94 64 ac 00 04 13 5b 56  |....//...d....[V|
00000010  4b 38 43 6a 38 c5 ba c6  31 47 5b 10 01 6d 5d 4c  |K8Cj8...1G[..m]L|
00000020  3c cd a8 cb 8a ab a8 94  8c e0 00 58 1c df 4e 95  |<..........X..N.|
00000030  9e 8a e8 39 f6 ac 6b 16  14 ef ff ff fa e8 57 e9  |...9..k.......W.|
00000040  80 e0 aa ae 38 44 df 18  52 6a de 76 10 86 31 12  |....8D..Rj.v..1.|
00000050  00 07 09 f4 6d 82 a3 40  9c 11 44 ca a7 d9 2b 1c  |....m..@..D...+.|
00000060  4e b7 df 25 d4 88 c5 a2  41 59 90 d6 9a 6e a6 4d  |N..%....AY...n.M|
00000070  79 45 20 e9 f8 55 d9 f7  67 63 d8 b2 64 f5 ae 3b  |yE ..U..gc..d..;|
00000080  aa f5 0f d3 db 43 b4 44  37 20 4f e9 5b 6c ff a6  |.....C.D7 O.[l..|
00000090  d8 f9 98 f1 fe 63 ec e7  7f a5 ef 6d 7f fb 3d bd  |.....c.....m..=.|
000000a0  5e e7 62 b3 fd e5 21 fc  4b f7 fa f6 f1 eb eb ff  |^.b...!.K.......|
000000b0  2b f7 72 48 1e c7 80 30  55 56 e2 a2 06 10 e3 a0  |+.rH...0UV......|
000000c0  d0 42 33 3d 58 1a 39 c6  7a 7b bd e8 a8 81 39 04  |.B3=X.9.z{....9.|
000000d0  3f 73 b9 18 e6 50 00 45  34 44 77 53 73 2a e1 c0  |?s...P.E4DwSs*..|
000000e0  c0 cd 2f d5 7f fa ee 20  b0 84 9a 04 17 bc ef e5  |../.... ........|
000000f0  a1 69 cc b8 85 4d 0b bf  bb fd f3 45 77 82 cd d8  |.i...M.....Ew...|
00000100  79 47 0a 4e 49 c0 08 0e  42 69 26 a4 0e 2c 84 ec  |yG.NI...Bi&..,..|
00000110  59 f8 37 25 ff 4e f4 8f  1a 8e f3 02 d4 0e 11 71  |Y.7%.N.........q|
00000120  79 31 99 07 56 a5 4c 57  64 11 59 29 8f 06 97 bb  |y1..V.LWd.Y)....|
00000130  52 6d d0 56 a3 78 9a 15  a3 9b 4c ca a9 42 4d 78  |Rm.V.x....L..BMx|
00000140  3d 41 ba 1a 2e 36 aa 92  12 f4 0e 83 d0 03 08 0e  |=A...6..........|
00000150  02 a1 e0 d6 c6 33 33 44  9d a3 c7 a3 f2 2a b4 e3  |.....33D.....*..|
00000160  8f 95 95 10 6a aa ef ac  47 2d be 2f f7 ae da 03  |....j...G-./....|
00000170  a9 6e a4 99 94 69 af a5  f4 e9 2f 9b ae d0 b8 91  |.n...i..../.....|
00000180  00 00 3d 2a aa f9 ff fb  94 64 a3 00 03 b1 5a 57  |..=*.....d....ZW|
00000190  b3 12 33 6a 4f 09 2a f6  24 a3 6d 0f 5d 79 65 4c  |..3jO.*.$.m.]yeL|
000001a0  35 0d a1 70 28 ac a4 63  a1 b4 a2 93 ce dd c9 d5  |5..p(..c........|
000001b0  2f d8 55 6e df 67 35 77  bb e5 33 fb 4e 6d 00 01  |/.Un.g5w..3.Nm..|
000001c0  c1 ff 07 fe ff ff 02 00  00 00 27 79 1a 06 00 fe  |..........'y....|
000001d0  ff ff 05 fe ff ff 29 79  1a 06 f0 62 a9 03 00 00  |......)y...b....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
/home/ubuntu/Downloads/boot_info_script.sh: line 1888: (  / 2 ) + 16 : syntax error: operand expected (error token is "/ 2 ) + 16 ")

```

---

### Post by coffeecat on 2011-12-09
The output of the boot script is most odd. If you look at the first part, it lists all your sda partitions and whatever operating systems and boot files it can find in them, but only partition 1, sdb1, from sdb. However your fdisk output, and the fdisk output in the boot script output, shows a number of sdb partitions, as does blkid in the boot script output.

The boot script should show the contents of any grub.cfg and /etc/fstab files it finds but does not. You have posted the contents of your /etc/fstab separately. How did you obtain that?

Another couple of inconsistencies: your sdb drive was originally sda when you installed Ubuntu to partition sda11 - but the UUID for the original sda11 is the same as the current sdb10. Also, the boot script shows evidence of a partition 10 with burg installed to it on sda, the 250GB drive, but there is no sda10. Did you at one time have Ubuntu installed on the 250GB drive?

---

### Post by BC59 on 2011-12-09
Well I'm going to be the bad and make the big suggestion.

If you still have working Windows (I really don't know how on these partitions) make an image .iso of your installation. Backup all your personal data and format the whole drive. Then reinstall Windows using the .iso image and leave enough space for your other installations.

I cannot think simpler and more working solution.

---

### Post by oldfred on 2011-12-09
I think script errored out on awk and some math function & missing data that it could not find with your more complicated install.

Try installing gawk and rerunning it to see if then it works better.

sudo apt-get install gawk

The grub 1.98 installed in sda is probably just looking for the partition 10 on sdb. My system showed the same type of issue with a install of grub to sda and it really booted from a high number partition on sdc. But that may now just be an obsolete install since you have 1.99 in sdb.

Script is not updated for the newest version of grub 1.99 and does not parse the partition core.img is looking for, so we cannot tell.

---

### Post by hariks0 on 2011-12-10
> **coffeecat said:**
> 

The boot script should show the contents of any grub.cfg and /etc/fstab files it finds but does not. You have posted the contents of your /etc/fstab separately. How did you obtain that?

From the /etc/fstab accessed with the live CD.:D
> 
Another couple of inconsistencies: your sdb drive was originally sda when you installed Ubuntu to partition sda11 - but the UUID for the original sda11 is the same as the current sdb10. Also, the boot script shows evidence of a partition 10 with burg installed to it on sda, the 250GB drive, but there is no sda10. Did you at one time have Ubuntu installed on the 250GB drive?

Yes. I have an Ubuntu installation there [Not sure about the location] :confused:

---

### Post by coffeecat on 2011-12-10
> **hariks0 said:**
> From the /etc/fstab accessed with the live CD.:D

That's good. That means that there is a viable partition. I wanted to check that you hadn't posted the contents of an archived fstab. :)

All I can suggest at the moment is to re-run the boot script with gawk installed as oldfred recommends.

---

### Post by hariks0 on 2011-12-11
\\:D/

In /etc/fstab, just replaced the UUID of partition mounted as /H with /dev/sda9 and voila...

There is no problem anymore...:popcorn:

Thank you folks for the support.

---

