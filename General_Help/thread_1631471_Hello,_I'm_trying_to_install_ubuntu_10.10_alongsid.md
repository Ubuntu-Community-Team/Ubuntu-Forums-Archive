---
title: "Hello, I'm trying to install ubuntu 10.10 alongside my windows 7 on my CQ10-525dx"
date: 2010-11-26
forum: General Help
---

### Post by xCasualty on 2010-11-26
Hello, I'm trying to install ubuntu 10.10 alongside my windows 7 on my CQ10-525dx Netbook.

I don't see the "Install alongside..." button so i clicked the advanced button.
My options are: 
sbd1(ntfs) 208.7B
sbd2(ntfs)233.9GB
sbd3(ntfs)15.8GB
sbd4(fat32)108.2MB


I'm trying to give ubuntu 80 GB partition along with the rest to my windows 7. How do I do this?

please give me step by step if possible. Thanks!

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda4: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       409,599       407,552   7 HPFS/NTFS
/dev/sda2             409,600   457,242,623   456,833,024   7 HPFS/NTFS
/dev/sda3         457,242,624   488,183,807    30,941,184   7 HPFS/NTFS
/dev/sda4         488,183,808   488,395,119       211,312   c W95 FAT32 (LBA)


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 7987 MB, 7987003392 bytes
104 heads, 8 sectors/track, 18749 cylinders, total 15599616 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             72    15,599,615    15,599,544   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        7CA6DB7DA6DB367C                       ntfs       SYSTEM                        
/dev/sda2        B68C97868C974033                       ntfs                                     
/dev/sda3        CA8ED4F88ED4DDCF                       ntfs       RECOVERY                      
/dev/sda4        12AE-5BFF                              vfat       HP_TOOLS                      
/dev/sda: PTTYPE="dos" 
/dev/sdb1        E8BC-5937                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 26 00  |.X.SYSLINUX...&.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 48 00 00 00  |........?...H...|
00000020  b8 07 ee 00 65 3b 00 00  00 00 00 00 02 00 00 00  |....e;..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 37 59 bc e8 4e  4f 20 4e 41 4d 45 20 20  |..)7Y..NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 30 74 16 00  66 ba 00 00 00 00 bb 00  |}.f.0t..f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by wilee-nilee on 2010-11-26
Four partitions is the max allowed on a single HD. 

Post the bootscript in my signature, post it in code tags as described in my signature as well. **This code tag stuff is very important**, if you can't figure that out just report yourself to the mods with the report button and ask them to do it for you.

---

### Post by xCasualty on 2010-11-26
I'm only trying to install Ubuntu alongside Windows 7.

Only 2 operating systems.

---

### Post by xCasualty on 2010-11-26
and I'm installing from a USB drive because my netbook doesn't have a CD drive. Someone give me step by step please

---

### Post by wilee-nilee on 2010-11-26
Look here is the deal your asking for easy help on what could be the process of making your computer a nice **doorstop**, do you get what I'm saying here follow my instructions.

---

### Post by xCasualty on 2010-11-26
obviously I don't understand what you said.....

---

### Post by wilee-nilee on 2010-11-26
> **xCasualty said:**
> obviously I don't understand what you said.....

Hmm so clicking on the link in my signature which takes you to a page with instructions is to much, well sorry I'm out of here this will just be a thread where I get frustrated with you not worth it to be honest.;)

---

### Post by onaridge on 2010-11-26
There is a ton of info if you Google it on doing this. I spent awhile reading about it and then did my installation. There are also YouTube videos. You should really do a bit of this research before doing it. Research about the kinds of partitions Ubuntu uses as well as your options for using one or two or even three Ubuntu partitions is all info that is good to know before you do this.

---

### Post by onaridge on 2010-11-26
This was a link I used, nice pictures and description: [http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)

---

### Post by ivarn on 2010-11-26
OK so I assume what you have here is; sbd1(ntfs) 208.7B partition is your bootloader,
your sbd2(ntfs)233.9GB partition is for video files, music files and stuff,
 your sbd3(ntfs)15.8GB partition is the windows installation 
and your sbd4(fat32)108.2MB must be something else.
Why would you setup your pc like this?

I have 3 partitions, 2 ntfs partitions and a ext4 partition for ubuntu.
My 2nd ntfs partition is where I put all my music, videos and all that stuff.

Ok, so what you should do here is, go to the windows 7 disk manager and re organize your setup. You obviously have 2 partitions you can combine into one.

---

### Post by Quackers on 2010-11-26
If you boot into Windows and go to the Disk Management console you will see details of your current disk layout. You currently have 4 partitions on your system -even though you only have one operating system. 

Please take note!!!! 

If all of those 4 partitions are Primary partitions (Disk Management will tell you if they are) do not try to create a fifth primary! If you do those partitions will change to SFS (dynamic disks) and then you won't be installing anything for some time!

If those existing partitions are all Primary you will need to delete one of them (after backing up whatever is in it) and then create an extended partition. This will allow for many more partitions to be created within that extended partition.

It is a sensible move to first post the bootscript info that willee-nillee suggested (look at the bottom of his post in his sig for the link).

---

### Post by xCasualty on 2010-11-26
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda4: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       409,599       407,552   7 HPFS/NTFS
/dev/sda2             409,600   457,242,623   456,833,024   7 HPFS/NTFS
/dev/sda3         457,242,624   488,183,807    30,941,184   7 HPFS/NTFS
/dev/sda4         488,183,808   488,395,119       211,312   c W95 FAT32 (LBA)


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 7987 MB, 7987003392 bytes
104 heads, 8 sectors/track, 18749 cylinders, total 15599616 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             72    15,599,615    15,599,544   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        7CA6DB7DA6DB367C                       ntfs       SYSTEM                        
/dev/sda2        B68C97868C974033                       ntfs                                     
/dev/sda3        CA8ED4F88ED4DDCF                       ntfs       RECOVERY                      
/dev/sda4        12AE-5BFF                              vfat       HP_TOOLS                      
/dev/sda: PTTYPE="dos" 
/dev/sdb1        E8BC-5937                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 26 00  |.X.SYSLINUX...&.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 48 00 00 00  |........?...H...|
00000020  b8 07 ee 00 65 3b 00 00  00 00 00 00 02 00 00 00  |....e;..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 37 59 bc e8 4e  4f 20 4e 41 4d 45 20 20  |..)7Y..NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 30 74 16 00  66 ba 00 00 00 00 bb 00  |}.f.0t..f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by xCasualty on 2010-11-26
Now what am I supposed to do with the RESULTS.txt????
BUMPING this to get a reply

---

### Post by Quackers on 2010-11-26
Allowing people time to read it would be good.
Have you checked whether your 4 partitions are primarys?

---

### Post by xCasualty on 2010-11-26
Sorry quackers,

How do I check if they are Primary?

the labels on them are: SYSTEM, RECOVERY, HP_TOOLS, and the last one that is 217GB is blank

I also have an unallocated that is 1MB?

---

### Post by xCasualty on 2010-11-26
sda1 = SYSTEM(199MB)
sda2 = blank(217.83GB)
sda3 = RECOVERY(14.75GB)
sda4 = HP_TOOLS (102.18
unallocated = (1MB)

---

### Post by Quackers on 2010-11-26
Have a look at the first sentence in post #11.
Windows > Disk Management console > are all partitions described as primary?

---

### Post by xCasualty on 2010-11-26
All four of the ones described are listed as TYPE: BASIC

---

### Post by Quackers on 2010-11-26
Can you post a screenshot of the Disk Management screen please? 
Use New Reply rather than quick reply and then Manage Attachments to upload the screenshot.

---

### Post by xCasualty on 2010-11-26
OOPS.

All four are marked BLUE which is Primary Partition. My apologies

---

### Post by xCasualty on 2010-11-26
If you sign into MSN messenger and add: [email]taddye@hotmail.com[/email] it may be easier for us to talk

---

### Post by xCasualty on 2010-11-26
Here's the screenshot

---

### Post by Quackers on 2010-11-26
Ok, so you have some choices to make.
1) To install another operating system as a dual boot you would need to delete one of those 4 partitions - obviously you would need to back up any needed data in there first! then create an extended partition. This will allow for the creation of many more partitions within that extended partition. Then in one of those new partitions you can replace the data you backed up into. Then you would be able to install a new operating system into the new partitions.

2) Install Ubuntu as a Wubi installation from within Windows - this will keep your present partition scheme intact.

3) Buy a new hard drive and install Ubuntu on that.

4) Install Ubuntu in a VMWare or VirtualBox environment - keeping your existing partition scheme.

5) Have a think about it, then decide it's not a good idea to continue.

Please bear in mind that partition changes and operating system installations carry risks with them. Data and whole systems can be lost!
I would really suggest that you read more about what you intend to do before you embark on that journey :-) Good luck and happy reading! :-)

---

### Post by xCasualty on 2010-11-26
Which Partition do I delete???

and why must I buy a new hard drive? I'm using a netbook

---

### Post by Quackers on 2010-11-26
> **xCasualty said:**
> Which Partition do I delete???

and why must I buy a new hard drive? I'm using a netbook

These are the choices you need to make.
You don't have to buy a new hard drive - it is a choice that you have.

---

### Post by xCasualty on 2010-11-26
Which partition would you delete? so that I could give ubuntu its own 80GB space

---

### Post by ivarn on 2010-11-26
You said the last one was blank. you mean empty, right?
If so, delete that one.

---

### Post by wilee-nilee on 2010-11-26
I have to state here that this thread is at 27 posts without the OP having a clue, sorry but that's the facts.

A experienced semi knowledgeable user could of had this done in maybe 5-6 posts.

Some basic homework needs to be done by the OP this is over their head in several areas.

Nothing personal here just some obvious facts.

This forum has awesome tutorials, but using a thread for this is not good practice, and has people like myself and the other user on here who knows this stuff backing away shaking our heads like a gunslinger in a old western. And the others who know this stuff just staying away.

---

### Post by xCasualty on 2010-11-27
ISSUE RESOLVED!


If you have the same problem I have, where your computer has 4 partitions at the beginning, this is what I did. 

Obviously I had to get rid of one of the partitions to create a new one. My options were, C, Recovery, System, and HP Tools.

[COLOR=Red]**C**[/COLOR] - All my files, so I wasn't going to delete this one.

[COLOR=Red]**Recovery** [/COLOR]- NEEDS to be kept in case you need to recover to a saved point

[COLOR=Red]**System**[/COLOR] - Has boot files for Windows 7, so I couldn't delete it.

[COLOR=Lime]**HP Tools**[/COLOR] - Includes Diagnostic tools for your computer. (These files are not necessary) So I deleted this one because I do not need diagnostic tools, which are used for telling you WHY your hard drive, RAM, or anything else fails or crashes. Not a very useful tool and if you want it back, you can download it from HP's website.

[U]
How to delete HP Tools or any other partition via Windows[/U]
1. Press Start
2. Type "Disk Manage" and click the link that appears in the start menu

Here, you will see all of the partitions on your Hard Drive

3. Right click on HP Tools(or any other hard drive) and press Delete


_Next Step: Defragging computer to maximize space for new partition_
1. Press Start
2. Type "Defrag"
3. Open the defragger
4. Run defrag on "C" only
5. Wait. This will take around 15-20 minutes


_After defrag is complete: Shrink the C Drive_
1. Press Start
2. Type "Disk Manage" and click the link that appears in he start menu
3. Right click on "C"
4. Press Shrink and wait. It will say "Querying.....please wait"
     When complete, there will be only ONE box you can type in.
5. Type in the amount in Mb that you want for your new partition. So type in 1024 for 1GB or 2048 for GB and so on... if you want to figure out how many Mb you need to type in, say for 80GB multiply 80 by 1024 and type that number in. WHEN YOU GET THIS NUMBER ADD 1500MB to it so whatever number you came up with ADD 1500MB
6. Press OK and wait.

_After Shrinking, install ubuntu_
1. Run installer
2. Click Specify partition
3. You will see TWO that are described as "Free Space", double click the one that is the amount you shrunk.
4.There is only one drop down box in the new window, click it and find, "Swap Area"
5. Type 1500 in the box
6. Press OK
7. You will see that the swap area was created, now double click the free space that we clicked before(it will be 1500 smaller)
8. Make sure the number typed in he box is the number left on the free space(it autofills so you probable won't have to worry about this step)
9. Make sure the "Ex4Journal...." is selected in the drop down.
10. Under Mount, type "/" (DON'T TYPE THE QUOTATIONS)
11. Press OK
12. Press Install Now
13. Follow instructions to install

Congratulations, ubuntu is installed :)

---

### Post by Quackers on 2010-11-27
Very nice :-)

---

### Post by xCasualty on 2010-11-27
> **wilee-nilee said:**
> I have to state here that this thread is at 27 posts without the OP having a clue, sorry but that's the facts.

A experienced semi knowledgeable user could of had this done in maybe 5-6 posts.

Some basic homework needs to be done by the OP this is over their head in several areas.

Nothing personal here just some obvious facts.

This forum has awesome tutorials, but using a thread for this is not good practice, and has people like myself and the other user on here who knows this stuff backing away shaking our heads like a gunslinger in a old western. And the others who know this stuff just staying away.


If you actually had some common sense, you would understand that it was my first installation. So hop the **** off my nuts about 5-6 posts to fix this issue. It was much more than that because I'm installing a new operating system. So if you want to make your own 5-6 post solution, go right ahead. Not stopping you smart ***.

---

### Post by onaridge on 2010-11-27
You can remove the recovery partition after you burn the recovery cd's. The partition is for restoring the computer to it's factory state and should not be confused with recovery points which are kept in the Windows folder. 

I did a very first installation just like you by going to the url I posted earlier and doing a little reading by searching this forum and using Google. Wilee could have been a bit more diplomatic but he is correct. All this info is already available for any beginner to follow because I recently did it successfully myself. :-)

---

### Post by xCasualty on 2010-11-27
> **onaridge said:**
> You can remove the recovery partition after you burn the recovery cd's. The partition is for restoring the computer to it's factory state and should not be confused with recovery points which are kept in the Windows folder. 

I did a very first installation just like you by going to the url I posted earlier and doing a little reading by searching this forum and using Google. Wilee could have been a bit more diplomatic but he is correct. All this info is already available for any beginner to follow because I recently did it successfully myself. :-)


only problem with your solution....

I'm using a netbook and can't burn a recovery CD
and it's very difficult to make a USB version

---

### Post by onaridge on 2010-11-27
then you are stuck with the partition unless you buy an external writer, you can get them anywhere from 25 bucks on up. Might be worth the investment as you might find yourself using it for more than just an install. :-)

---

### Post by dougalkerr on 2010-11-27
Just to add some balance here; I posted almost exactly the same as your 'Issue Resolved' post several months ago to aid someone else.
Perhaps a little more searching to start with may have saved you some grief although I admit it can be difficult to get the words correct for the search engine and find the correct solution from it.

So at least you should now have a dual booting system? Yes?

---

### Post by wilee-nilee on 2010-11-27
> **xCasualty said:**
> If you actually had some common sense, you would understand that it was my first installation. So hop the **** off my nuts about 5-6 posts to fix this issue. It was much more than that because I'm installing a new operating system. So if you want to make your own 5-6 post solution, go right ahead. Not stopping you smart ***.

[SIZE="5"][COLOR="Red"]You removed the notation that you wanted no partitions removed,[/COLOR][/SIZE] you had to be hand led through the whole process, look man take your misdirected anger out on your self where it belongs. Nothing I posted was wrong. Your really only mad at me because I was correct from the beginning and you don't like being called out for just being well I can't post the words here but lets just say misinformed.

I will say though I'm glad you got it fixed, if you spend anytime on the forums you will understand after a while why I said 5 or 6 posts. Basically without the bootscript we couldn't tell where all the pertinent booting files are, just getting you to read the instructions was very difficult. Once that was posted it was a easy fix. In the second post of the thread I told you 4 primary partitions was the limit. **I was a great help to you and you don't even realize it.**

How would you have liked it if somebody told you to remove the wrong partition that may of had the bootfiles in it eh.

Also I doubt that recovery partition will work now I hope so but once you add a additional bootloader its use is basically gone in most cases. The recovery partition was probably used in conjunction with the HP tools partition removed.

---

### Post by xCasualty on 2010-11-28
> **wilee-nilee said:**
> [SIZE="5"][COLOR="Red"]You removed the notation that you wanted no partitions removed,[/COLOR][/SIZE] you had to be hand led through the whole process, look man take your misdirected anger out on your self where it belongs. Nothing I posted was wrong. Your really only mad at me because I was correct from the beginning and you don't like being called out for just being well I can't post the words here but lets just say misinformed.

I will say though I'm glad you got it fixed, if you spend anytime on the forums you will understand after a while why I said 5 or 6 posts. Basically without the bootscript we couldn't tell where all the pertinent booting files are, just getting you to read the instructions was very difficult. Once that was posted it was a easy fix. In the second post of the thread I told you 4 primary partitions was the limit. **I was a great help to you and you don't even realize it.**

How would you have liked it if somebody told you to remove the wrong partition that may of had the bootfiles in it eh.

Also I doubt that recovery partition will work now I hope so but once you add a additional bootloader its use is basically gone in most cases. The recovery partition was probably used in conjunction with the HP tools partition removed.




[SIZE="7"][COLOR="Red"]No you.[/COLOR][/SIZE]

---

