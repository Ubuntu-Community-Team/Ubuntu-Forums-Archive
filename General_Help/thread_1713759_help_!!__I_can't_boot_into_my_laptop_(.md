---
title: "help !!  I can't boot into my laptop :("
date: 2011-03-24
forum: General Help
---

### Post by Mohd.a on 2011-03-24
[SIZE=3]Hi all ,

I put my laptop into suspend and the battery died.
Now it will not boot.
I get:

mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting / sys/ on root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or dirctory
Target filesystem doesn't have /sbin/init.

and i get :

BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)

(initramfs)

You can see the photo



please ,

I want my file .


[/SIZE]

---

### Post by Rubi1200 on 2011-03-24
Hi and welcome to the forums :-)

Please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Mohd.a on 2011-03-24
[SIZE=2]How many time for it ?

half hour with this message

Identifying MBRs...
Computing Partition Table of /dev/sda...
Computing Partition Table of /dev/sdb...
Searching sda1 for information... 


[/SIZE]

---

### Post by Rubi1200 on 2011-03-24
Hmm, it should only take a few seconds to scan and generate the results.

This *might* indicate some serious file-system damage. Do you have backups of important data?

Let's try something else;

download and burn to CD this distro called Slax:
[http://distrowatch.com/table.php?distribution=slax](http://distrowatch.com/table.php?distribution=slax)

Then, boot the computer with it as a LiveCD and follow the instructions I gave you before with one exception; you do not need to use sudo because the terminal on Slax uses root privileges by default.

Thanks.

---

### Post by Mohd.a on 2011-03-24
[SIZE=2]No , I don't have backups of data.

and I don't have driver for Live CD , can i use ( Slax ) by flash

[/SIZE]

---

### Post by Rubi1200 on 2011-03-24
Yes, I think it is possible to use a flash drive. You need to use something like UNetbootin:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by Mohd.a on 2011-03-24
thank you Rubi1200

I installed ( Slax ) in flash .

but i can't access to the internet.

What after that ?

---

### Post by Mohd.a on 2011-03-24
any body help me !! :( :(

---

### Post by Rubi1200 on 2011-03-25
How do you normally connect to the Internet; wireless or wired?

---

### Post by Mohd.a on 2011-03-25
Hello Rubi1200

by wireless

---

### Post by Rubi1200 on 2011-03-25
If you are on the Slax live distro you are unable to connect? Let me check for you about how to connect, but I will also upload a copy of the file you need so you can access it from here.

Yeah, wireless can be a bit of a pain on Slax. Try going to the main menu > Internet > Wireless Manager and see if it recognizes and can connect. Otherwise, can you plug the ethernet cable in just for this session?

---

### Post by Mohd.a on 2011-03-25
RESULTS.txt

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'ext4'

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000ee7a8

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   224,827,391   224,825,344  83 Linux
/dev/sda2         224,829,438   234,440,703     9,611,266   5 Extended
/dev/sda5         224,829,440   234,440,703     9,611,264  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2021 MB, 2021654528 bytes
255 heads, 63 sectors/track, 245 cylinders, total 3948544 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x04dd5721

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     3,948,543     3,948,481   c W95 FAT32 (LBA)


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 4005 MB, 4005527552 bytes
32 heads, 63 sectors/track, 3880 cylinders, total 7823296 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x24ed131c

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63     7,822,079     7,822,017   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        592a734d-5c0f-416d-824a-1835e162025a   ext4                                     
/dev/sda5        e9d70e1b-cb92-4896-8f96-d42ca4bd861f   swap                                     
/dev/sdb1        07EE-0C57                              vfat       PENDRIVE                      
/dev/sdc1        17F7-2A1D                              vfat       PENDRIVE                      

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw,si=ec329d6f,xino=/mnt/live/memory/xino/.aufs.xino,nowarn_perm)
/dev/sdb1        /mnt/sdb1                vfat       (rw,noatime,quiet,umask=0,check=s,shortname=mixed)
/dev/sdc1        /mnt/sdc1                vfat       (rw)


=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: boot/initrd.gz
    .0GB: boot/vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  5f 9a be 99 b2 14 8f d1  84 04 14 3b 12 f8 e8 6c  |_..........;...l|
00000010  a1 1b b4 80 0b 4c b2 ac  cc 0e 43 47 86 df 46 70  |.....L....CG..Fp|
00000020  8e ed 50 b1 4d 45 61 b5  a5 98 45 4a 00 e3 dd 8a  |..P.MEa...EJ....|
00000030  44 90 06 3b cb 6e 69 d9  59 f3 6c 8b 34 30 42 69  |D..;.ni.Y.l.40Bi|
00000040  30 02 91 27 9b 88 19 91  79 a7 c2 38 0a eb 0e 92  |0..'....y..8....|
00000050  e6 75 e0 8c f3 c2 87 28  10 13 cf 0a 7e a0 34 fe  |.u.....(....~.4.|
00000060  05 49 7d 40 2f 32 ea bd  ff 6f 89 a0 4d 4a 97 c0  |.I}@/2...o..MJ..|
00000070  6a 3e 14 9a c0 ac 12 f0  78 98 10 3d f1 81 ac 62  |j>......x..=...b|
00000080  a7 6f 49 3c ad 47 6c 2b  be 30 6d e4 e4 b3 85 fe  |.oI<.Gl+.0m.....|
00000090  87 98 60 18 50 e4 9f 4e  78 f5 82 b8 10 ec d8 b9  |..`.P..Nx.......|
000000a0  0c 23 19 52 5b 40 db 65  b6 d9 fb 21 b1 a1 1a 03  |.#.R[@.e...!....|
000000b0  d3 65 a0 0d c6 24 8a df  78 f5 04 ce 93 74 61 13  |.e...$..x....ta.|
000000c0  d6 9b 2c 41 3d 47 80 9d  40 1a 9a cd 22 4e 9c a2  |..,A=G..@..."N..|
000000d0  0f 57 a1 13 33 71 6c d1  53 40 c8 54 e7 85 e8 00  |.W..3ql.S@.T....|
000000e0  16 41 a3 f3 50 26 47 b7  d5 cc 33 d2 23 53 bd 1c  |.A..P&G...3.#S..|
000000f0  f1 55 f2 5a 30 90 ca ba  06 41 2f 08 94 91 a2 20  |.U.Z0....A/.... |
00000100  ae e3 81 70 66 ac ee 4c  fa 10 21 41 73 6b 08 bb  |...pf..L..!Ask..|
00000110  34 cb 6c 93 e2 d9 86 17  ab 14 6d 6d 5c 12 ee 49  |4.l.......mm\..I|
00000120  b7 17 f4 03 98 39 88 db  0f da 15 3c 59 f9 e6 28  |.....9.....<Y..(|
00000130  92 5e f0 79 db 25 32 ac  96 6e 1f 2a d4 d5 34 9e  |.^.y.%2..n.*..4.|
00000140  7e 9a 3a cd a8 c1 08 5e  e0 16 eb 48 66 c6 93 a2  |~.:....^...Hf...|
00000150  6a 98 02 ba ff 24 da 5c  a3 9f 7a 4a 00 1b 58 75  |j....$.\..zJ..Xu|
00000160  3a cd 9d f1 e0 2a 02 02  b8 fa 60 ca 48 68 c6 39  |:....*....`.Hh.9|
00000170  26 ee 4c ea c3 ad db 11  28 a6 32 57 19 1e d9 6f  |&.L.....(.2W...o|
00000180  2b 20 fd 82 0b ed 8c 91  71 99 90 e9 9a 19 f7 c1  |+ ......q.......|
00000190  16 6c 5c 61 42 93 6d cc  d2 ca 55 3f 81 07 1c 58  |.l\aB.m...U?...X|
000001a0  7d aa 6f 17 e8 7d 16 ad  63 cd 8e 6f 7f 9d 4a 7b  |}.o..}..c..o..J{|
000001b0  71 7b c1 30 6f 79 09 80  da fa 0b de 28 5b 00 fe  |q{.0oy......([..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 a8 92 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdc1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 04 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  c1 5a 77 00 72 3b 00 00  00 00 00 00 02 00 00 00  |.Zw.r;..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 1d 2a f7 17 4e  4f 20 4e 41 4d 45 20 20  |..).*..NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 1e 56  8e c1 b1 26 bf 78 7b f3  |.v{R.W.V...&.x{.|
00000070  a5 8e d9 bb 78 00 0f b4  37 0f a0 56 20 d2 78 1b  |....x...7..V .x.|
00000080  31 c0 b1 06 89 3f 89 47  02 f3 64 a5 8a 0e 18 7c  |1....?.G..d....||
00000090  88 4d bc 50 50 50 50 cd  13 eb 5c 8b 55 aa 8b 75  |.M.PPPP...\.U..u|
000000a0  a8 c1 ee 04 01 f2 81 fa  b7 07 73 2b f6 45 b4 7f  |..........s+.E..|
000000b0  75 25 38 4d b8 74 20 66  3d 21 47 50 54 75 10 80  |u%8M.t f=!GPTu..|
000000c0  7d b8 ed 75 0a 66 ff 75  ec 66 ff 75 e8 eb 0f 51  |}..u.f.u.f.u...Q|
000000d0  51 66 ff 75 bc eb 07 51  51 66 ff 36 1c 7c b4 08  |Qf.u...QQf.6.|..|
000000e0  cd 13 72 13 20 e4 75 0f  c1 ea 08 42 89 16 1a 7c  |..r. .u....B...||
000000f0  83 e1 3f 89 0e 18 7c fb  bb aa 55 b4 41 8a 16 74  |..?...|...U.A..t|
00000100  7b cd 13 72 10 81 fb 55  aa 75 0a f6 c1 01 74 05  |{..r...U.u....t.|
00000110  c6 06 45 7d 00 66 b8 08  77 00 00 66 ba 00 00 00  |..E}.f..w..f....|
00000120  00 bb 00 7e e8 10 00 66  81 3e 24 7e d4 ff 73 72  |...~...f.>$~..sr|
00000130  75 76 ea 38 7e 00 00 66  03 06 60 7b 66 13 16 64  |uv.8~..f..`{f..d|
00000140  7b b9 10 00 eb 2b 66 52  66 50 06 53 6a 01 6a 10  |{....+fRfP.Sj.j.|
00000150  89 e6 66 60 b4 42 e8 7f  00 66 61 8d 64 10 72 01  |..f`.B...fa.d.r.|
00000160  c3 66 60 31 c0 e8 70 00  66 61 e2 da c6 06 45 7d  |.f`1..p.fa....E}|
00000170  2b 66 60 66 0f b7 36 18  7c 66 0f b7 3e 1a 7c 66  |+f`f..6.|f..>.|f|
00000180  f7 f6 31 c9 87 ca 66 f7  f7 66 3d ff 03 00 00 77  |..1...f..f=....w|
00000190  17 c0 e4 06 41 08 e1 88  c5 88 d6 b8 01 02 e8 37  |....A..........7|
000001a0  00 66 61 72 01 c3 e2 c9  31 f6 8e d6 bc 68 7b 8e  |.far....1....h{.|
000001b0  de 66 8f 06 78 00 be df  7d e8 09 00 31 c0 cd 16  |.f..x...}...1...|
000001c0  cd 19 f4 eb fd 66 60 ac  20 c0 74 09 b4 0e bb 07  |.....f`. .t.....|
000001d0  00 cd 10 eb f2 66 61 c3  8a 16 74 7b cd 13 c3 42  |.....fa...t{...B|
000001e0  6f 6f 74 20 65 72 72 6f  72 0d 0a 00 00 00 00 00  |oot error.......|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

hda 
=============================== StdErr Messages: ===============================

mdadm: No arrays found in config file


```

---

### Post by Rubi1200 on 2011-03-25
According to the results there is probably damage to the file-system:

> mount: unknown filesystem type 'ext4'

The best thing to do would be a file-system check:

```
e2fsck -f -y -v /dev/sda1
```

Again, do this from Slax and then reboot when it is finished, taking out the flash drive, and keep your fingers crossed that you can boot Ubuntu again.

Let me know what happens please or if there are errors, post them here.

---

### Post by Mohd.a on 2011-03-25
thank you very much

I reboot my system without any errors .

Thank you rubi for help me.

---

### Post by Rubi1200 on 2011-03-25
No problem, you are more than welcome :)

Please mark this thread Solved using the Thread Tools near the top of the page.

---

