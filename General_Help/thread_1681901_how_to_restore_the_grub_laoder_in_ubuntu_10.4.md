---
title: "how to restore the grub laoder in ubuntu 10.4"
date: 2011-02-04
forum: General Help
---

### Post by connect2jan on 2011-02-04
hi
sorry i know that sudo,i didnt use ,sorry for that
i have small questions
1q):; in ubuntu if grub (loader) has been currepted,while booting it will show grub>(has gone)
so how to reload/restore the grub instead of installing linux(ubuntu) again.
----------------------------------------------------------------------------------

2)q::  in ubuntu if grub has been currepted,while booting it will show grub>(has gone)
if i have some imp data in ubuntu ,i want take data back.so using linux live cd(i used but i didnt see the data,i think we have mount to /mnt then we will see/access/copy the data) ,how to see/access /copy the data
------------------------------------------------------------------------------
3q)::same question grub has been cuurepted,if i have duel boot(windows+ubuntu),instead of installing ubutntu/ubutnu grub loader,can we do only windows as working(means i decided to remove the ubuntu , i want use the only windows,without distrubence the windows data(if i have some data in windows))

---

### Post by Lessian on 2011-02-05
I am in basically the same situation: need to know how to access important files, how to restore or re-install grub without re installing linux. I only have the one OS installed so cant access that way.
any leads would be helpful.

---

### Post by Rubi1200 on 2011-02-05
Hi and welcome to the forums connect2jan and Lessian :-)

The best advice I can offer right now is that you both follow these instructions:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by connect2jan on 2011-02-06
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    41,986,047    41,984,000   7 HPFS/NTFS
/dev/sda2          41,986,048   156,301,311   114,315,264   5 Extended
/dev/sda5          41,988,096   113,668,095    71,680,000  83 Linux
/dev/sda6         113,670,144   115,718,143     2,048,000  82 Linux swap / Solaris
/dev/sda7         115,732,323   156,296,384    40,564,062  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4012 MB, 4012900352 bytes
255 heads, 63 sectors/track, 487 cylinders, total 7837696 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     7,837,695     7,837,633   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        78E4F98A7CC40453                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda6        2373bd4f-b3c5-4f57-9b16-3736535ab1ee   swap                                     
/dev/sda7        57cfa62a-f0e3-4349-9de8-d3e3f585d7ed   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        9E59-52A3                              vfat       New Volume                    
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda7        /mnt/tmp                 ext4       (rw)
/dev/sdb1        /media/New Volume        vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  e7 c0 83 7e 1a ee 24 3e  5d d6 0b ad 79 37 3f e4  |...~..$>]...y7?.|
00000010  f0 63 f7 0a 90 69 b3 32  2c e3 10 b5 a9 87 b9 00  |.c...i.2,.......|
00000020  11 79 e8 26 6d 07 3e b6  b5 dc 75 e9 be 75 5a 06  |.y.&m.>...u..uZ.|
00000030  1d 86 cf a5 20 d9 d5 ba  0f 66 2f 16 dc ad de 3f  |.... ....f/....?|
00000040  e0 8c 4a ec 87 fc 3a 97  30 1c 7c 9b af ef 26 3c  |..J...:.0.|...&<|
00000050  df 91 0a df b7 cd f8 77  33 7b 55 4e 7b c7 02 ee  |.......w3{UN{...|
00000060  12 28 69 f1 d3 bc 36 f0  9a d1 64 be b5 87 fb 07  |.(i...6...d.....|
00000070  fb 63 13 a5 59 c2 a9 40  d3 9c c6 d8 d7 c1 7c c5  |.c..Y..@......|.|
00000080  eb b2 9f 5d 93 41 c8 2e  89 c4 47 b3 e0 b4 f6 36  |...].A....G....6|
00000090  55 d5 9d 94 7a 6e 15 67  52 70 0c b4 ac e7 e7 ca  |U...zn.gRp......|
000000a0  82 fd 3b 19 1d 0c d7 f8  42 9e 75 96 f5 37 ec 82  |..;.....B.u..7..|
000000b0  04 c5 bb 98 0f 46 a4 c4  9b ff c6 22 d1 d7 de de  |.....F....."....|
000000c0  f8 53 55 6b 17 60 e9 b3  18 07 66 6e a3 e1 e1 a8  |.SUk.`....fn....|
000000d0  74 da ed b3 4a 3b 7b 85  3b 7c 69 01 63 9c 9c d8  |t...J;{.;|i.c...|
000000e0  cf b0 41 31 ea e3 c0 85  7b 7f fa 8e f9 df 52 2d  |..A1....{.....R-|
000000f0  fc 6c a0 76 ef d9 4d c6  66 b0 38 9d c9 93 0f e2  |.l.v..M.f.8.....|
00000100  2a 9b ad c9 d3 e4 5f 25  de d3 7d a2 78 e1 64 33  |*....._%..}.x.d3|
00000110  2f b7 7a 9a 94 42 84 1b  15 4e d3 d7 42 43 ec 06  |/.z..B...N..BC..|
00000120  38 1d 87 54 9d 50 55 8a  80 e1 6b b9 03 47 df 2f  |8..T.PU...k..G./|
00000130  dc a7 9f 75 ac 44 6d b0  28 7a fd 9a c1 b6 42 5d  |...u.Dm.(z....B]|
00000140  1b 18 4d e9 c4 a6 89 0c  73 be 79 bd f7 f9 71 e0  |..M.....s.y...q.|
00000150  0e c4 0d 3e 3d 13 c0 c7  0e 72 a2 6d 1d e9 57 3a  |...>=....r.m..W:|
00000160  7a 26 f9 39 42 2f 6c 63  e3 8f 87 7d f3 37 bf ea  |z&.9B/lc...}.7..|
00000170  1b 7b 77 db 19 14 61 22  e6 fb ca e3 bf 09 f7 f4  |.{w...a"........|
00000180  d3 02 da ed fa 2e c1 d0  12 7a 44 9c 80 58 1a 34  |.........zD..X.4|
00000190  dd 5d 34 5e 34 53 20 82  cd a1 ac 3b 4a 26 d9 93  |.]4^4S ....;J&..|
000001a0  56 77 29 6c d0 d0 45 f8  ed 82 59 db d5 fa 36 c9  |Vw)l..E...Y...6.|
000001b0  71 c1 64 d6 56 6e 1e bd  17 4e 7b 0c 1a 2f 00 fe  |q.d.Vn...N{../..|
000001c0  ff ff 83 fe ff ff 00 08  00 00 00 c0 45 04 00 fe  |............E...|
000001d0  ff ff 05 fe ff ff 00 c8  45 04 00 48 1f 00 00 00  |........E..H....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sda5

00000000  82 0b e2 78 f0 7c 71 35  e9 ad 41 dc 3e 0d 3e cf  |...x.|q5..A.>.>.|
00000010  f8 fa d0 a4 3b 5a bd 8e  00 08 25 cf ab 98 8c 20  |....;Z....%.... |
00000020  6f 12 aa 11 12 0d 8e db  da 42 71 cb f8 64 06 10  |o........Bq..d..|
00000030  cf 2b 0d 32 cc 3b a3 2c  8d 15 46 17 7f 63 f2 03  |.+.2.;.,..F..c..|
00000040  ce ba fd 18 0d c7 cb 67  a1 65 0c 8b 03 8f 67 87  |.......g.e....g.|
00000050  8b f4 e8 99 a9 91 f6 72  10 51 c9 15 39 90 2f b8  |.......r.Q..9./.|
00000060  b0 ad fe fb 74 43 1b 0e  2a d6 ec d0 dd ba 60 5d  |....tC..*.....`]|
00000070  1e e3 6b f7 74 37 fc ef  68 e9 97 a0 00 66 62 54  |..k.t7..h....fbT|
00000080  d8 d4 a8 99 f2 c0 90 25  a1 b7 51 ce 71 87 cf 1a  |.......%..Q.q...|
00000090  7d 16 b9 9e bb 05 fc a9  cd 33 70 91 f1 8b 8b 6a  |}........3p....j|
000000a0  f2 06 e4 b4 74 63 b5 2e  19 88 bf 17 72 83 15 9c  |....tc......r...|
000000b0  69 57 59 97 97 ac 6f 87  b6 c7 77 ca c9 f6 07 4b  |iWY...o...w....K|
000000c0  5e 32 45 c3 c8 ff 22 b2  ee 0b 0c d7 4d b4 23 38  |^2E...".....M.#8|
000000d0  88 bd fb 0a 31 32 8e 49  5f 7e 35 1d 5f b3 31 34  |....12.I_~5._.14|
000000e0  c9 af f5 3d 5e f2 70 5e  7e c2 ce 12 ac 3e 82 2e  |...=^.p^~....>..|
000000f0  87 5f ff 32 5e ec 57 df  58 5d d3 e2 99 7a e8 83  |._.2^.W.X]...z..|
00000100  ea dd 68 57 f8 21 6c 89  11 70 49 cb d6 3b a0 32  |..hW.!l..pI..;.2|
00000110  0b ab 8d 0f 1e d7 17 e5  a5 ad ec 34 e9 95 52 7f  |...........4..R.|
00000120  65 5e cd d6 28 80 50 27  5a db 78 23 ef 99 bb ac  |e^..(.P'Z.x#....|
00000130  3f 32 20 a0 9a e0 da 68  12 90 c9 99 d6 01 eb 52  |?2 ....h.......R|
00000140  91 70 1f a2 9c 2b a9 c5  95 44 cd 60 21 a2 da f0  |.p...+...D.`!...|
00000150  6d 7e 85 fa 0d fd 26 f8  0a e8 6a bb 5f 80 0a fa  |m~....&...j._...|
00000160  82 b2 aa 33 61 4d 24 4a  94 0a d9 06 84 4e bb f8  |...3aM$J.....N..|
00000170  82 2a ac 18 9c 46 99 91  0b 56 5b a1 ac 59 1f f6  |.*...F...V[..Y..|
00000180  ea 4c a7 80 d8 f3 7e 03  4d 8f 5d 4c 39 fc 95 01  |.L....~.M.]L9...|
00000190  67 ba fb 5f 5b f9 2f 52  c2 89 75 ab 4f ff bd b1  |g.._[./R..u.O...|
000001a0  a3 7c ee 77 07 6d cd 79  97 c8 34 70 87 4e 91 4f  |.|.w.m.y..4p.N.O|
000001b0  6e c7 4f 39 6e ff f3 fa  85 6f aa cc a1 89 43 b3  |n.O9n....o....C.|
000001c0  77 b9 56 94 3e 39 0a 16  71 9e 49 e6 ca d2 54 e2  |w.V.>9..q.I...T.|
000001d0  79 42 2c e0 eb e8 d4 58  3a 90 fc 4b a2 77 af 9d  |yB,....X:..K.w..|
000001e0  9d 86 75 30 db 82 e3 30  68 d2 80 11 c0 8e 3f 9d  |..u0...0h.....?.|
000001f0  c0 82 51 48 ef bd 41 1b  62 d8 80 06 2b b5 1d c1  |..QH..A.b...+...|
00000200

hi this i got RESULTS.txt

---

### Post by Rubi1200 on 2011-02-06
Hi and thanks for the results connect2jan.

I am a little bit concerned by these results because I do not see the boot files for Windows or the Ubuntu install.

It seems that whatever you tried to do failed.

Do you have a Windows recovery CD?

Do you have the Ubuntu CD?

---

### Post by connect2jan on 2011-02-07
hi
 rubi1200,
ya that first line isfollowing
"No boot loader is installed in the MBR of /dev/sda"


instead of--


"Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in  partition #6 for /boot/grub."
i did
---sudo fdisk -l
---sudo mount /dev/sda7/mnt(linux installed-ubuntu)
--sudo grub-install --root-directory=/mnt /dev/sda
after this foll msg came
 "installation finished,no error reported""
--then i did-Reboot
but still """grub >" is coming ,its not booting

---

### Post by Rubi1200 on 2011-02-07
Hi,
perhaps I was not clear enough before.

There is no operating system defined on sda7 and on sda6 there are errors.

Are you sure Ubuntu installed correctly?

Are you able to mount the partitions and see files from the LiveCD?

---

### Post by glene77is on 2011-02-07
Rubi,
Good advice.   :)
Run the Live_CD and navigate to the (alleged) Ubuntu install OS.
Something should show, else the install failed. 
The Live-CD has the Gparted application, which can mount, list info.

---

### Post by connect2jan on 2011-02-15
hi 
glene,rubi

ya in my system ubutnu was installed on /dev/sda7,so

i mounted this partition to mnt using follwing command
' mount /dev/sda7 /mnt"
i am seeing only dir are::boot,dev,grub,lost+found proc
means ubuntu was installed on /dev/sda7 na?
i tried restore the grub ,but again same error

---

### Post by Rubi1200 on 2011-02-15
Are you able to mount and see any files on sda1 or sda5?

Again, take a look at the script results; there are no boot files or operating systems defined so either the results are incorrect or there is something wrong with the installs of both Windows and Ubuntu.

---

### Post by r3dempt1on on 2011-02-15
to fix grub simply download the non live cd version of ubuntu, burn it to a disc and boot from it

when it boots there will be an option to repair corrupt ubuntu install.
select it.
it will take you through steps like the original install did.
once you get to the partitions, select the one where grub was installed and select reinstall grub(if you dont know just go down the list, it wont let you install over a partition that has something besides grub on it)
a progress bar will show up followed by an option to reboot. 
reboot and your install will work

---

### Post by glene77is on 2011-02-15
> **r3dempt1on said:**
> 
to fix grub 
simply download the   [SIZE=2][COLOR=Red]non_Live-CD   [/COLOR][/SIZE]version of ubuntu, 
burn it to a disc and boot from it


r3, 
Interesting.   :)
Hope you return with a few more comments on this approach.

---

### Post by PaulReaver on 2011-02-15
if your ubuntu is only installed on one partition ie / and on sda1

boot into a live cd and

sudo mkdir /mnt/temp
sudo mount /dev/sda1 /mnt/temp
sudo chroot /mnt/temp

sudo update-grub

exit

sudo shutdown -r now


I think it should fix it....?   its been a while since i've had to do this.

---

