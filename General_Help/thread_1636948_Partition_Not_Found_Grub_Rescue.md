---
title: "Partition Not Found Grub Rescue"
date: 2010-12-03
forum: General Help
---

### Post by HaGGardSmurf on 2010-12-03
I uninstalled ubuntu from my main HDD, and its now on a different HDD.

Anyhow, when I turn on my computer I get:

Partition not found
Grub Rescue

I've used my windows disk and repaired my mbr and boot (bootrec /fixmbr bootrec /fix mbr) multiple times, yet I always get this problem.

Only way I can boot windows is if I leave my install disk in my drive. It will say press any key to boot from cd / dvd I just wait a couple seconds, and it boots into windows.

Without the disk, I get the grub problem.

I have only 1 partition on my HDD, and that is my windows 7 partition, nothing else. Help?!

---

### Post by drs305 on 2010-12-03
If you run the boot info script from the following link we can see the status of your boot files.

[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

Please post the contents of RESULTS.txt between 'code' tags, which you generate by clicking the # icon in the post's menubar.

After running the Windows repair programs, are you sure you BIOS is booting your Windows drive first?

---

### Post by HaGGardSmurf on 2010-12-03
I just skimmed through the log, and I see windows XP. I want to mention XP is installed on a seperate HDD, which is a 320 GB HDD, it is not setup in raid or anything, just simply plugged in, I kind of use it as extra space, and use XP sometimes, buy just manually booting from my other HDD. (As my main HDD has a higher boot priority than my 320 GB HDD.)

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdc1 and 
                       looks at sector 1227405177 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   625,121,279   625,121,217   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          2,048 1,465,144,583 1,465,142,536   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        DC8C77C88C779C28                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb         1046-1B4D                              vfat       PENDRIVE                      
/dev/sdc1        C060627A606276D6                       ntfs                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb         /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 22 07  |.X.SYSLINUX...".|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 00 00 00  |........?.......|
00000020  00 38 f2 00 6f 3c 00 00  00 00 00 00 02 00 00 00  |.8..o<..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 4d 1b 46 10 4e  4f 20 4e 41 4d 45 20 20  |..)M.F.NO NAME  |
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
00000100  7d 00 66 b8 e0 27 16 00  66 ba 00 00 00 00 bb 00  |}.f..'..f.......|
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

(PS I dont have ubuntu installed, I booted from a live usb)

---

### Post by drs305 on 2010-12-03
My reply will mostly be just to 'bump' your thread as I don't know much about Windows.

A few thoughts though. I believe W7 sometimes boots through a previous install (not sure about XP) if it was present when W7 was installed. You might try booting the drive with XP first to see if that transfers control to 7.

You mentioned moving drives around. I also have seen posts about W7 not liking being moved - changing drive orders, etc. You might check into that as well.

Otherwise, I hope a Windows user happens along and offers you some more concrete advice. Good luck.

---

### Post by HaGGardSmurf on 2010-12-03
When I boot my comp, and manually select a boot device (my 320 gb HDD with xp) it boots XP.

I havent moved any drives, my 2 HDD's have stayed plugged into the same sata ports since I bought my 750 GB HDD about 9 months ago.

I appreciate the response though!

Hopefully someone know's how to fix this.

Why is grub still listed on there? Thats what doesnt make sense to me? It should be gone?

Thing is when I installed ubuntu I had to do the manual method of partitioning where you select your swap space, and select what partition to install on etc.

Anyways for bootloader I selected my windows 7 boot loader as opposed to just my 750 gb HDD. So anyhow I think that may be the issue? My comp tries to boot windows 7 like it used to but grub is installed where windows 7 boot loader used to be? I'm quite certain the windows xp home edition thing in the log is my windows 7 boot loader.

Reason I say that is because when I installed ubuntu I had to use my recovery disk to make me able to boot into win 7, and to boot into win 7 I had to select windows xp home edition in the grub menu, if I clicked windows 7 in grub, I would get a black screen for a second, then grub would load again... (Making me think it would boot what it thought was win 7 but was actually grub.)

---

### Post by wilee-nilee on 2010-12-03
sdc1: _________________________________________________________________________

    File system:       ntfs
    [B]Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdc1 [/B]and 
                       looks at sector 1227405177 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

So although the script reads as the MS bootloader in sdc and the W7=sdc1 showing the correct (boot on its own) set up it is attached to the sda XP boot. Although grub doesn't show in the last stanza=Boot files/dirs: it still says there is a grub2 in the bootloader.

Now I could try and give you the solutions but there are others who just know more and will probably be responding soon.

So it would be helpful to know what you have as far as backups, if you need the XP at all, and what install discs you have, and how much your willing to just reinstall in a orderly fashion to just get it in a much stabler state. This can be fixed most likely, but you have a more complex setup then you need even with XP, and W7 together.

---

### Post by drs305 on 2010-12-03
> **HaGGardSmurf said:**
> Why is grub still listed on there? Thats what doesnt make sense to me? It should be gone?

Thing is when I installed ubuntu I had to do the manual method of partitioning where you select your swap space, and select what partition to install on etc.

Anyways for bootloader I selected my windows 7 boot loader as opposed to just my 750 gb HDD. So anyhow I think that may be the issue? My comp tries to boot windows 7 like it used to but grub is installed where windows 7 boot loader used to be? I'm quite certain the windows xp home edition thing in the log is my windows 7 boot loader.

Reason I say that is because when I installed ubuntu I had to use my recovery disk to make me able to boot into win 7, and to boot into win 7 I had to select windows xp home edition in the grub menu, if I clicked windows 7 in grub, I would get a black screen for a second, then grub would load again... (Making me think it would boot what it thought was win 7 but was actually grub.)

You've analyzed it pretty well. Grub2 got installed on the sdc1 partition  (normally it should only be installed to the MBR). The MBR is most likely passing control to XP, then on to sdc1. Why your Windows repair disks aren't fixing it I don't know. 

You could disconnect your XP drive. I would expect that W7 could very well handle the repair in that case, although I am not sure how you would get XP back. You'd probably then have to disconnect the W7 drive to repair XP. If you got them both working independently, Ubuntu/Grub could probably piece it all back together again.

You can always go to a Windows forum, I'm sure they would know.

---

### Post by wilee-nilee on 2010-12-03
> **drs305 said:**
> You've analyzed it pretty well. Grub2 got installed on the sdc1 partition  (normally it should only be installed to the MBR). The MBR is most likely passing control to XP, then on to sdc1. Why your Windows repair disks aren't fixing it I don't know. 

You could disconnect your XP drive. I would expect that W7 could very well handle the repair in that case, although I am not sure how you would get XP back. You'd probably then have to disconnect the W7 drive to repair XP. If you got them both working independently, Ubuntu/Grub could probably piece it all back together again.

You can always go to a Windows forum, I'm sure they would know.

So these commands are not correct
> **HaGGardSmurf said:**
> (bootrec /fixmbr bootrec /fix mbr)  

Could be just a abbreviation but it should be ```
bootrec.exe /fixmbr
```

Here is the whole set OP just for reference.

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
BootRec.exe /fixmbr (#updates MBR master boot record...do not run if you still want grub)
chkdsk /r
BootRec.exe /FixBoot (#updates PBR partition boot)
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

Notice the http address to the W7 forums but it seems your familiar with getting to the repair command line in W7. Can't guarantee the saving of XP or anything here really, but the correct commands should be in a easy access area I thought.

We open source users are command line users a lot of the time so if we see a command that looks wrong we generally comment, but I recognize that the OP might have just abbreviated the bootrec.exe /fmbr command.

Then we also have a program called testdisc which can be used to clean out grub in a ntfs setup, so lets wait for the ones with a definitive answer I would say.

---

### Post by oldfred on 2010-12-04
wilee-nilee already gave you the fixboot windows way.

A couple of versions ago the grub install was very confusing (meaning worse than it is now) and many users installed grub to the windows partition. meierfra, the author of the boot info script created several repair pages using Linux tools to fix issues.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

The XP install in sda1 shows the boot sector has been modified to be win7 and it also has both the win7 boot files with BCD and XP boot files with boot.ini. When booting sda do you not get a win7 boot not a XP boot.ini boot?

---

### Post by HaGGardSmurf on 2010-12-04
Thing is windows XP has never been installed on this HDD, or booted from it.

XP is on another HDD, and I only boot it by F8'ing and manually selecting the other HDD to boot from, I dont know why its included on this hard drive.

It must be because grub scanned all my HDD's and added windows XP to the boot list.

Anyways, I had to use the repair disk after I installed ubuntu because I couldnt boot win 7, so after I put in the disk it scanned automatically and said it automatically repaired my win 7 boot info, I also manually fixed mbr and boot. Then to boot win 7 I had to select XP through grub.

bootrec.exe /fixboot and bootrec /fixboot both are the same command, so that's not the issue.

What it all boils down to is grub got installed over my windows 7 boot loader, and I think grub made a windows XP boot loader, which when I tried to repair windows 7, it installed over that.

So win 7 boot loader = grub
windows xp = windows 7

I only want windows 7 boot info, nothing else, no xp, no grub.

---

### Post by oldfred on 2010-12-04
I think the issue is more Windows. Windows can only boot from one copy of windows as it uses the boot flag to know what partition to boot from. If you have multiple installs of windows it moves the boot files from the second install and combines the boot either into boot.ini for XP or the BCD for Vista or Win7.

Grub will look for certain windows boot files and try to set up a boot stanza for that windows partition.

To understand a little more about how windows works:
To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

---

### Post by HaGGardSmurf on 2010-12-05
I dont want to dual boot anything.

To boot into XP, I just select my other HDD and boot from it.

All I want is to have my computer boot into windows when I turn it on. So I guess I would be basically re-creating my boot partition table... How would I do this?

---

### Post by oldfred on 2010-12-05
You may be able to unplug one drive and then do windows repairs so windows does not find the other install. But once windows finds the other install it is difficult to remove. You can manually edit the boot.ini and BCD and literally copy the boot files to the correct windows root. Not sure of all the details as it is more windows related.

---

