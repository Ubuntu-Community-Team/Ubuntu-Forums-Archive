---
title: "Setting Windows bootloader... GParted unknown filesys"
date: 2011-12-26
forum: General Help
---

### Post by Mark201 on 2011-12-26
Ok so long story short (sort of), I had a Windows 7/Ubuntu dualboot. I needed to remove Ubuntu so I thought it'd be an okay idea to just remove the Ubuntu partition using GParted. I did that and I merged the newly freed partition with my existing Windows partition.
 
When I then rebooted my laptop, I just got a GRUB error saying "No such partition". I did a bit of Googling and found out that I needed to make sure my computer booted from the Windows bootloader. Most websites said I could do this simply enough using the Windows CD, but I don't have a Windows CD (the laptop is actually a friend's who got it from their college with Windows installed, which they loaned to me). I found a website saying I could do it with the Ubuntu CD either (which I did have):
 
[http://robert.penz.name/221/mini-howto-restore-windows-mbrbootloader-with-linux/](http://robert.penz.name/221/mini-howto-restore-windows-mbrbootloader-with-linux/)
 
So I ran the Ubuntu trial from the CD. I wasn't able to access the internet from that due to an issue with drivers, so I downloaded syslinux onto a USB stick from another computer and copied it onto the trial Ubuntu and installed. 
 
At this moment, the last time I ran GParted I had three partitions. One 1MB of unallocated space. One small partition "sda1" that had the boot flag set. And a partition "sda2" which was the biggest and had ~37GB of 'used' space. This corresponded with the space used by my files. Both sda1 and sda2 were of file system ntsf.
 
I then ran the command suggested at the link above:
 
*"sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda1".*
 
(Put in "sda1" because I assumed that's what I should have put in, since that had the boot flag in GParted).
 
The same "no such partition" error came up when I rebooted. Running GParted, I see sda1 is of file system "unknown" now.
 
Then, perhaps foolishly, I re-ran the Ubuntu trial version and ran the above command but put in "sda2" instead. Now, both sda1 and sda2 are of file system "unknown" and under the 'used' column, they are both "--".
I've included a screenshot.
 
 
Anyone know what to do from here???
 
I've back up all important files, however I really really don't want to lose the Windows install. It will cause a lot of hassle. I borrowed this laptop from a friend for a few months and the install was done by their college.
 
Anyway, if there's anything I can do to get the install back (which must still be on the harddrive!) let me know.
 
Or if I'm fecked and should just reformat the harddrive feel free to tell me that too.
 
Any feedback at all would be great!!
 
As mentioned I borrowed the laptop from a friend. The reason why I was uninstalling Ubuntu was that I need to return it asap.
 
[IMG]http://i51.tinypic.com/5mc043.jpg[/IMG]

---

### Post by oldfred on 2011-12-26
You do not install Linux or even the Window MBR boot loader to a PBR - partition boot sector. All NTFS partitions have to have a PBR with the NTFS signature. Since it sounds like you may have written to it twice? then the backup it also keeps may not be recoverable. If you only wrote once it may be recoverable. The NTFS partition also has to have size info that matches the partition table, so when you resized it from outside Windows you corrupted the PBR.

Check first with Testdisk to see if you can recover the backup. If not use testdisk to create a NTFS BS - boot sector, but that is just so Windows will be able to repair it as it often does not want to repair a PBR that is totally corrupted.

As described, it has an option to "Recover NTFS boot sector from its backup"
If Backup BS isn't available, choose RebuildBS. 
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

If backup works, then you are ok. If not you will need a Windows repairCD and run BootRec.exe /FixBoot & chkdsk possibly more than once as both depend on the other.

---

### Post by jjex22 on 2011-12-26
I think you're at use a windows disk to reinstall. - the dd command is very risky, and should have been described as such in the post - it copys and converts the data from target to source with no warnings. The guide was aimed at over writing the mbr (sda) with syslinux, but instead i suspect you've overwriten the partitions by dd-ing to sda1 and 2, data recovery would be able to recover nearly everything as the bin file is so small, but I think you'll have to reinstall windows to get it booting again. then use your backup or a recovery tool such as [photorec]("http://www.cgsecurity.org/wiki/PhotoRec") to get your stuff back. 

Always be careful with dd, its incredibly valuable and useful, but very risky - before gui tools replaced it is earned the nickname "Disk Destroyer" for this very reason. The guide really should have mentioned this as I say.

For future referance, by far the easiest way to go back to just plain windows is to boot into windows, download and install easyBCD, set it to only boot windows 7 with 0 timeout then use gparted to erase the linux partition. If you want to then add a distro again, use gparted to make the space, install the bootloader to the / or /boot partition, not the mbr and then add entry for it in easy BCD.

Good luck getting it going again.

---

### Post by Mark201 on 2011-12-26
Thanks for the responses. I think it's clear now that I misread the instructions that I was reading from in the link provided!
 
Anyway I've got the testdisk to do its searching. I don't think it has found the partition where all my windows files were. I've taken pictures of the screens it showed me.
 
When I first ran the testdisk analyse, it gave me this screen:
 
[IMG]http://i55.tinypic.com/15zk3ea.jpg[/IMG] 
 
Judging from the 'tutorial' that you linked, does this mean that it is detecting both the old AND new partitions that I'm trying to find?
 
But anyway, after doing the search, the first screen I saw was this:
 
[IMG]http://i53.tinypic.com/210ka6h.jpg[/IMG]
 
Saying a certain Linux partition could not be recovered. On I went to the next screen...
 
[IMG]http://i54.tinypic.com/24nqvcn.jpg[/IMG]
 
The above picture shows me a few partitions it found. I've pressed 'p' on them all... the 'Linux' one is the linux partition I intentionally deleted earlier. The partition with "[HP_RECOVERY]" beside it seems to be from an install done in 2010. The newest file on there is from 2nd April 2011. It seems like the first one may be of interest? It says at the bottom that it was found using the backup sector. The files in that are:
 
[IMG]http://i54.tinypic.com/2ni1grb.jpg[/IMG]
 
Whatever that means....
 
 
But is this any use without the main Windows partition that didn't turn up?
 
 
Any suggestions what I should do next?
 
Thanks again for all your help so far.
 
If only I hadn't misread that instruction, I could be tucked up in bed by now... :(

---

### Post by Mark201 on 2011-12-26
Just updated the post above with an extra screenshot! I don't want to do anything without feedback on this just in case I mess things up even more!

---

### Post by oldfred on 2011-12-27
It looks like it has two copies of the same info which I have not seen enough recoveries from testdisk to know but seems like it could. And the partition 1 of 100MB or 204800 looks about like the standard 100MB boot/repair partition Windows 7 normally has. I would try to recover it.

You will also need to have boot flag on that partition. Not sure if that is error or if it also says the NTFS BS boot sector also is not correct?

If it is saying drive is too small you may also have another partition error. But see if testdisk will let you recover partition 1 first.

It may be best to post this:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

---

### Post by Mark201 on 2011-12-27
Thanks for replying again.

Below is my results.txt.

I will attempt to recover partition 1 now.

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   625,137,344   624,930,497   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  fa 31 c0 8e d8 8e d0 bc  00 7c 89 e6 06 57 52 8e  |.1.......|...WR.|
00000010  c0 fb fc bf 00 06 b9 00  01 f3 a5 ea 20 06 00 00  |............ ...|
00000020  52 b4 41 bb aa 55 31 c9  30 f6 f9 cd 13 72 13 81  |R.A..U1.0....r..|
00000030  fb 55 aa 75 0d d1 e9 73  09 66 c7 06 8d 06 b4 42  |.U.u...s.f.....B|
00000040  eb 15 5a b4 08 cd 13 83  e1 3f 51 0f b6 c6 40 f7  |..Z......?Q...@.|
00000050  e1 52 50 66 31 c0 66 99  e8 66 00 e8 21 01 4d 69  |.RPf1.f..f..!.Mi|
00000060  73 73 69 6e 67 20 6f 70  65 72 61 74 69 6e 67 20  |ssing operating |
00000070  73 79 73 74 65 6d 2e 0d  0a 66 60 66 31 d2 bb 00  |system...f`f1...|
00000080  7c 66 52 66 50 06 53 6a  01 6a 10 89 e6 66 f7 36  ||fRfP.Sj.j...f.6|
00000090  f4 7b c0 e4 06 88 e1 88  c5 92 f6 36 f8 7b 88 c6  |.{.........6.{..|
000000a0  08 e1 41 b8 01 02 8a 16  fa 7b cd 13 83 c4 10 66  |..A......{.....f|
000000b0  61 c3 e8 c4 ff be be 7d  bf be 07 b9 20 00 f3 a5  |a......}.... ...|
000000c0  c3 66 60 89 e5 bb be 07  b9 04 00 31 c0 53 51 f6  |.f`........1.SQ.|
000000d0  07 80 74 03 40 89 de 83  c3 10 e2 f3 48 74 5b 79  |..t.@.......Ht[y|
000000e0  39 59 5b 8a 47 04 3c 0f  74 06 24 7f 3c 05 75 22  |9Y[.G.<.t.$.<.u"|
000000f0  66 8b 47 08 66 8b 56 14  66 01 d0 66 21 d2 75 03  |f.G.f.V.f..f!.u.|
00000100  66 89 c2 e8 ac ff 72 03  e8 b6 ff 66 8b 46 1c e8  |f.....r....f.F..|
00000110  a0 ff 83 c3 10 e2 cc 66  61 c3 e8 62 00 4d 75 6c  |.......fa..b.Mul|
00000120  74 69 70 6c 65 20 61 63  74 69 76 65 20 70 61 72  |tiple active par|
00000130  74 69 74 69 6f 6e 73 2e  0d 0a 66 8b 44 08 66 03  |titions...f.D.f.|
00000140  46 1c 66 89 44 08 e8 30  ff 72 13 81 3e fe 7d 55  |F.f.D..0.r..>.}U|
00000150  aa 0f 85 06 ff bc fa 7b  5a 5f 07 fa ff e4 e8 1e  |.......{Z_......|
00000160  00 4f 70 65 72 61 74 69  6e 67 20 73 79 73 74 65  |.Operating syste|
00000170  6d 20 6c 6f 61 64 20 65  72 72 6f 72 2e 0d 0a 5e  |m load error...^|
00000180  ac b4 0e 8a 3e 62 04 b3  07 cd 10 3c 0a 75 f1 cd  |....>b.....<.u..|
00000190  18 f4 eb fd 20 72 65 61  64 20 65 72 72 6f 72 20  |.... read error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200

Unknown BootLoader on sda2

00000000  fa 31 c0 8e d8 8e d0 bc  00 7c 89 e6 06 57 52 8e  |.1.......|...WR.|
00000010  c0 fb fc bf 00 06 b9 00  01 f3 a5 ea 20 06 00 00  |............ ...|
00000020  52 b4 41 bb aa 55 31 c9  30 f6 f9 cd 13 72 13 81  |R.A..U1.0....r..|
00000030  fb 55 aa 75 0d d1 e9 73  09 66 c7 06 8d 06 b4 42  |.U.u...s.f.....B|
00000040  eb 15 5a b4 08 cd 13 83  e1 3f 51 0f b6 c6 40 f7  |..Z......?Q...@.|
00000050  e1 52 50 66 31 c0 66 99  e8 66 00 e8 21 01 4d 69  |.RPf1.f..f..!.Mi|
00000060  73 73 69 6e 67 20 6f 70  65 72 61 74 69 6e 67 20  |ssing operating |
00000070  73 79 73 74 65 6d 2e 0d  0a 66 60 66 31 d2 bb 00  |system...f`f1...|
00000080  7c 66 52 66 50 06 53 6a  01 6a 10 89 e6 66 f7 36  ||fRfP.Sj.j...f.6|
00000090  f4 7b c0 e4 06 88 e1 88  c5 92 f6 36 f8 7b 88 c6  |.{.........6.{..|
000000a0  08 e1 41 b8 01 02 8a 16  fa 7b cd 13 83 c4 10 66  |..A......{.....f|
000000b0  61 c3 e8 c4 ff be be 7d  bf be 07 b9 20 00 f3 a5  |a......}.... ...|
000000c0  c3 66 60 89 e5 bb be 07  b9 04 00 31 c0 53 51 f6  |.f`........1.SQ.|
000000d0  07 80 74 03 40 89 de 83  c3 10 e2 f3 48 74 5b 79  |..t.@.......Ht[y|
000000e0  39 59 5b 8a 47 04 3c 0f  74 06 24 7f 3c 05 75 22  |9Y[.G.<.t.$.<.u"|
000000f0  66 8b 47 08 66 8b 56 14  66 01 d0 66 21 d2 75 03  |f.G.f.V.f..f!.u.|
00000100  66 89 c2 e8 ac ff 72 03  e8 b6 ff 66 8b 46 1c e8  |f.....r....f.F..|
00000110  a0 ff 83 c3 10 e2 cc 66  61 c3 e8 62 00 4d 75 6c  |.......fa..b.Mul|
00000120  74 69 70 6c 65 20 61 63  74 69 76 65 20 70 61 72  |tiple active par|
00000130  74 69 74 69 6f 6e 73 2e  0d 0a 66 8b 44 08 66 03  |titions...f.D.f.|
00000140  46 1c 66 89 44 08 e8 30  ff 72 13 81 3e fe 7d 55  |F.f.D..0.r..>.}U|
00000150  aa 0f 85 06 ff bc fa 7b  5a 5f 07 fa ff e4 e8 1e  |.......{Z_......|
00000160  00 4f 70 65 72 61 74 69  6e 67 20 73 79 73 74 65  |.Operating syste|
00000170  6d 20 6c 6f 61 64 20 65  72 72 6f 72 2e 0d 0a 5e  |m load error...^|
00000180  ac b4 0e 8a 3e 62 04 b3  07 cd 10 3c 0a 75 f1 cd  |....>b.....<.u..|
00000190  18 f4 eb fd 20 72 65 61  64 20 65 72 72 6f 72 20  |.... read error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200




```

---

### Post by Mark201 on 2011-12-27
Ok, something weird has happened. First of all the screen I showed you that said "Invalid NTFS boot" is no longer appearing.
 
Also, it appears that the NTFS partition in question has now changed to FAT32. See picture here:
 
[IMG]http://i56.tinypic.com/35m2uch.jpg[/IMG]
 
Also when I turn on my laptop and allow it to go to the GRUB rescue screen, it now says "Unknown filesystem" where it previously said "No such partition". I don't know what to do with this. Does it need to be changed back to NTFS somehow??
 
Also I'll have a Windows 7 ISO on my USB stick soon so I will be able to use that if needs be.

---

### Post by Mark201 on 2011-12-27
Ok I re-ran the boot info script again because I thought I might get different results since that filesystem change, and I did. It seems to be recognising a Windows 7 partition (sda2) and an Ubuntu partition. It also seems to have found the Ubuntu GRUB settings that used to appear when I turned on my laptop before I removed Ubuntu?!

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for /boot/grub.
 => MS-DOS 3.30 through Windows 95 (A) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot.ini /KERNEL.SYS /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *    160,000,000   162,047,999     2,048,000   c W95 FAT32 (LBA)
/dev/sda2         163,999,744   202,736,367    38,736,624   7 NTFS / exFAT / HPFS
/dev/sda3         343,730,176   613,629,951   269,899,776  83 Linux
/dev/sda4         613,629,954   625,153,409    11,523,456   f W95 Extended (LBA)
/dev/sda5         613,632,000   625,141,743    11,509,744  82 Linux swap / Solaris

/dev/sda4 ends after the last sector of /dev/sda

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1993 MB, 1993342976 bytes
2 heads, 63 sectors/track, 30898 cylinders, total 3893248 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32     3,893,247     3,893,216   6 FAT16


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        3B20-5946                              vfat       DIABLO_D
/dev/sda2        640A7BD30A7BA12A                       ntfs       
/dev/sda3        66fc0624-4fd4-4030-a429-e9ee1042c9bf   ext4       
/dev/sda5        85f984a9-3eff-41c8-83d1-0af5d11df44e   swap       
/dev/sdb1        4092-4670                              vfat       MARK CISCO

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/MARK CISCO        vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
D:\Avldr.bin="Avlgo - EFIBOOT_quick.img" 
--------------------------------------------------------------------------------

=========================== sda3/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 66fc0624-4fd4-4030-a429-e9ee1042c9bf
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 66fc0624-4fd4-4030-a429-e9ee1042c9bf
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-36-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 66fc0624-4fd4-4030-a429-e9ee1042c9bf
    linux    /boot/vmlinuz-2.6.32-36-generic root=UUID=66fc0624-4fd4-4030-a429-e9ee1042c9bf ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-36-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-36-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 66fc0624-4fd4-4030-a429-e9ee1042c9bf
    echo    'Loading Linux 2.6.32-36-generic ...'
    linux    /boot/vmlinuz-2.6.32-36-generic root=UUID=66fc0624-4fd4-4030-a429-e9ee1042c9bf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-36-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-35-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 66fc0624-4fd4-4030-a429-e9ee1042c9bf
    linux    /boot/vmlinuz-2.6.32-35-generic root=UUID=66fc0624-4fd4-4030-a429-e9ee1042c9bf ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-35-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-35-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 66fc0624-4fd4-4030-a429-e9ee1042c9bf
    echo    'Loading Linux 2.6.32-35-generic ...'
    linux    /boot/vmlinuz-2.6.32-35-generic root=UUID=66fc0624-4fd4-4030-a429-e9ee1042c9bf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-35-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-34-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 66fc0624-4fd4-4030-a429-e9ee1042c9bf
    linux    /boot/vmlinuz-2.6.32-34-generic root=UUID=66fc0624-4fd4-4030-a429-e9ee1042c9bf ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-34-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-34-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 66fc0624-4fd4-4030-a429-e9ee1042c9bf
    echo    'Loading Linux 2.6.32-34-generic ...'
    linux    /boot/vmlinuz-2.6.32-34-generic root=UUID=66fc0624-4fd4-4030-a429-e9ee1042c9bf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-34-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 66fc0624-4fd4-4030-a429-e9ee1042c9bf
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=66fc0624-4fd4-4030-a429-e9ee1042c9bf ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 66fc0624-4fd4-4030-a429-e9ee1042c9bf
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=66fc0624-4fd4-4030-a429-e9ee1042c9bf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 66fc0624-4fd4-4030-a429-e9ee1042c9bf
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 66fc0624-4fd4-4030-a429-e9ee1042c9bf
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 8CACCBD9ACCBBC48
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=66fc0624-4fd4-4030-a429-e9ee1042c9bf /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=85f984a9-3eff-41c8-83d1-0af5d11df44e none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 246.045970917 = 264.189849600  boot/grub/core.img                             1
 236.277420044 = 253.700947968  boot/grub/grub.cfg                             1
 246.055587769 = 264.200175616  boot/initrd.img-2.6.32-21-generic              1
 246.074485779 = 264.220467200  boot/initrd.img-2.6.32-34-generic              1
 246.164539337 = 264.317161472  boot/initrd.img-2.6.32-35-generic              1
 246.301399231 = 264.464113664  boot/initrd.img-2.6.32-36-generic              1
 246.034511566 = 264.177545216  boot/vmlinuz-2.6.32-21-generic                 1
 246.059352875 = 264.204218368  boot/vmlinuz-2.6.32-34-generic                 1
 246.157085419 = 264.309157888  boot/vmlinuz-2.6.32-35-generic                 1
 246.282085419 = 264.443375616  boot/vmlinuz-2.6.32-36-generic                 1
 246.301399231 = 264.464113664  initrd.img                                     1
 246.164539337 = 264.317161472  initrd.img.old                                 1
 246.282085419 = 264.443375616  vmlinuz                                        1
 246.157085419 = 264.309157888  vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  eb 58 90 46 72 65 65 44  4f 53 20 00 02 08 26 00  |.X.FreeDOS ...&.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 68 89 09  |........?....h..|
00000020  00 40 1f 00 cd 07 00 00  00 00 00 00 02 00 00 00  |.@..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 46 59 20 3b 4e  4f 20 4e 41 4d 45 20 20  |..)FY ;NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fc fa 29 c0 8e d8  |  FAT32   ..)...|
00000060  bd 00 7c b8 e0 1f 8e c0  89 ee 89 ef b9 00 01 f3  |..|.............|
00000070  a5 ea 7a 7c e0 1f 00 00  60 00 8e d8 8e d0 8d 66  |..z|....`......f|
00000080  e0 fb 88 56 40 be c1 7d  e8 f4 00 66 31 c0 66 89  |...V@..}...f1.f.|
00000090  46 44 8b 46 0e 66 03 46  1c 66 89 46 48 66 89 46  |FD.F.f.F.f.FHf.F|
000000a0  4c 66 8b 46 10 66 f7 6e  24 66 01 46 4c b8 00 02  |Lf.F.f.n$f.FL...|
000000b0  3b 46 0b 74 08 01 c0 ff  06 34 7d eb f3 66 8b 46  |;F.t.....4}..f.F|
000000c0  2c 66 50 e8 94 00 72 4d  c4 5e 76 e8 b7 00 31 ff  |,fP...rM.^v...1.|
000000d0  b9 0b 00 be f1 7d f3 a6  74 15 83 c7 20 83 e7 e0  |.....}..t... ...|
000000e0  3b 7e 0b 75 eb 4a 75 e0  66 58 e8 34 00 eb d2 26  |;~.u.Ju.fX.4...&|
000000f0  ff 75 09 26 ff 75 0f 66  58 29 db 66 50 e8 5a 00  |.u.&.u.fX).fP.Z.|
00000100  72 0d e8 80 00 4a 75 fa  66 58 e8 14 00 eb ec 8a  |r....Ju.fX......|
00000110  5e 40 ff 6e 76 be ee 7d  e8 64 00 30 e4 cd 16 cd  |^@.nv..}.d.0....|
00000120  19 06 57 53 89 c7 c1 e7  02 50 8b 46 0b 48 21 c7  |..WS.....P.F.H!.|
00000130  58 66 c1 e8 07 66 03 46  48 bb 00 20 8e c3 29 db  |Xf...f.FH.. ..).|
00000140  66 3b 46 44 74 07 66 89  46 44 e8 38 00 26 80 65  |f;FDt.f.FD.8.&.e|
00000150  03 0f 26 66 8b 05 5b 5f  07 c3 66 3d f8 ff ff 0f  |..&f..[_..f=....|
00000160  73 15 66 48 66 48 66 0f  b6 56 0d 66 52 66 f7 e2  |s.fHfHf..V.fRf..|
00000170  66 5a 66 03 46 4c c3 f9  c3 31 db b4 0e cd 10 ac  |fZf.FL...1......|
00000180  3c 00 75 f5 c3 52 56 57  66 50 89 e7 6a 00 6a 00  |<.u..RVWfP..j.j.|
00000190  66 50 06 53 6a 01 6a 10  89 e6 8a 56 40 b4 42 cd  |fP.Sj.j....V@.B.|
000001a0  13 89 fc 66 58 73 08 50  30 e4 cd 13 58 eb d9 66  |...fXs.P0...X..f|
000001b0  40 03 5e 0b 73 07 8c c2  80 c6 10 8e c2 5f 5e 5a  |@.^.s........_^Z|
000001c0  c3 4c 6f 61 64 69 6e 67  20 46 72 65 65 44 4f 53  |.Loading FreeDOS|
000001d0  20 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  | ...............|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 4e 6f  |..............No|
000001f0  20 4b 45 52 4e 45 4c 20  20 53 59 53 00 00 55 aa  | KERNEL  SYS..U.|
00000200

Unknown BootLoader on sda4

00000000  35 73 34 95 d3 86 78 74  21 16 c7 3c 81 47 10 b1  |5s4...xt!..<.G..|
00000010  3a 67 0f 3d 97 8e d1 25  19 91 30 4a 1f 9d cd 09  |:g.=...%..0J....|
00000020  78 55 fa e8 93 56 ab ad  f9 ab 45 ed 8e 75 47 b0  |xU...V....E..uG.|
00000030  56 f6 9d 72 50 61 97 f4  2a cb 47 88 f1 b8 9e 16  |V..rPa..*.G.....|
00000040  3e 29 38 f3 51 14 9c 6e  6f 10 a3 27 f0 16 3b 45  |>)8.Q..no..'..;E|
00000050  18 11 82 c7 18 45 4c d1  a6 ba 47 fd 9a b3 69 13  |.....EL...G...i.|
00000060  d9 33 a3 b5 3b 5d af d8  69 cf 7b a7 01 23 31 27  |.3..;]..i.{..#1'|
00000070  e1 3b 0e 38 a9 99 9f 99  5d c3 99 8e 06 f9 1c 33  |.;.8....]......3|
00000080  d0 04 72 08 6e de 41 13  d0 23 60 65 15 9e ec c1  |..r.n.A..#`e....|
00000090  53 29 a7 43 7f d5 4b 9b  e9 12 0b b1 8a 1c 6e 2d  |S).C..K.......n-|
000000a0  5c d4 e8 21 3b b6 4c 52  8b 89 da 7c 56 9a 54 3c  |\..!;.LR...|V.T<|
000000b0  d5 06 31 0a 42 44 b6 ec  3f cb f0 1c 68 9b c2 5f  |..1.BD..?...h.._|
000000c0  7e e8 17 8a ae f1 6c 90  7f 21 e5 26 9a 4e f4 17  |~.....l..!.&.N..|
000000d0  4e 17 28 fa d1 5f be dd  a0 65 4d 81 03 7d 82 88  |N.(.._...eM..}..|
000000e0  46 09 25 14 08 ea 58 55  f6 f0 e2 87 b3 1d aa 22  |F.%...XU......."|
000000f0  45 8f cf 2d a0 8e 2d 2a  4a e3 48 52 b4 b6 e1 a6  |E..-..-*J.HR....|
00000100  8a c7 d1 81 7c a3 26 1a  42 1b 60 a9 e3 a1 ec 33  |....|.&.B.`....3|
00000110  04 12 86 2c b3 6d 87 81  7c 36 91 6f 66 06 d4 4d  |...,.m..|6.of..M|
00000120  0c 22 44 7b 22 3d cf 20  ba 59 91 ec 8e 06 eb cd  |."D{"=. .Y......|
00000130  78 4c 16 35 5a 90 c1 03  da ba e4 c4 08 8f de b2  |xL.5Z...........|
00000140  04 3f 55 68 92 f7 e3 96  bc 43 4c e0 0a 57 9e 25  |.?Uh.....CL..W.%|
00000150  f5 14 a2 10 f0 a0 a5 a9  22 42 02 27 24 b6 a3 21  |........"B.'$..!|
00000160  f9 af bf 66 4b 49 c5 cb  05 a1 75 31 90 82 27 20  |...fKI....u1..' |
00000170  0c 2e a1 4b 32 4e c0 2e  8a 42 8e a8 42 a8 54 91  |...K2N...B..B.T.|
00000180  74 8f 50 21 ab 54 04 e9  8a 22 7a 86 06 e1 a2 ae  |t.P!.T..."z.....|
00000190  9c 1b 6e 10 11 f5 c1 f9  f5 06 2f 55 10 8a b5 6f  |..n......./U...o|
000001a0  b7 93 09 41 5d 09 5e 49  b1 10 b5 75 57 a7 9d 64  |...A].^I...uW..d|
000001b0  77 5b 66 ea fa a2 1f 24  e9 e7 99 71 ed 83 00 fe  |w[f....$...q....|
000001c0  ff ff 82 fe ff ff fe 07  00 00 f0 9f af 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

---

### Post by oldfred on 2011-12-27
I though sda1 might be the Windows 7 boot partition, but it looks like a DOS partition. Did you have DOS? The boot.ini looks like it is from XP but command.com is DOS?

If all the Windows boot files are in sda2, you need boot flag on sda2 for Windows repairs. You do not have to move flag for grub to boot it, if it is otherwise ok.

You show the sda2 partition and it shows all 3 of the normal Windows 7 boot files. It shows no errors but sometimes Windows 7 needs chkdsk or fixBoot to repair the partition. Script only checks that it is NTFS and has a valid code at the end of the boot sector. Windows wants NTFS partitions to have the size and info on which boot loader to use in the partition to boot.

Does Windows boot from sda2 entry in the grub menu? If not repairs. Sometimes pressing f8 just after enter on the grub line gets you into the Windows repair console. Some say you have to press very quickly or at same time or try several times. If that does not work you need a separate Windows repair CD or USB.

If you get into the repair console you should make this. If you cannot get into it you need one of these. Do you know someone with the same 32 or 64 bit version of Windows.

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by Mark201 on 2011-12-27
Ok I've finally run Windows from my USB, and went into the repairs section. A window popped up saying it found problems, and asks if I want to apply repairs. When I click on 'View' details it gives me another window. Here's a picture:
 
[IMG]http://i56.tinypic.com/34ec5qd.jpg[/IMG]
 
Should I click 'Repair and Restart'?
 
Or should I check to see if I can get Windows to boot from GRUB like you mentioned in your post?
 
Thanks for sticking with me, I'd be really lost without your help!
 
 
On DOS: I don't know if the laptop has had DOS on it before. It's a relatively new laptop so I'd be surprised, but as I said a friend got it from College so there may have been DOS on it in a previous lifetime and I wouldn't know!
 
EDIT - Just on your question about Windows booting from sda2 on the GRUB menu, I'm not sure how I should check that? When I turn my laptop on it still goes straight to the 'grub rescue' screen.
 
Also, I have Windows 7 Professional on my USB stick. I THINK that the version I had of Windows was Windows Ultimate. Should that make any difference?

---

### Post by oldfred on 2011-12-27
I have used Windows 7 repairUSB to run chkdsk on XP. Chkdsk does not matter on version. I think the auto repairs needs to be the same 32bit or 64bit version. Do change with gparted or Windows repair to move boot flag (active partition in Windows) to your Windows 7 partition.

The auto repair often takes 3 trys as it only fixes some things on each try. One of those will be to put the Windows boot loader into the MBR, so be prepared to reinstall grub2's boot loader to the MBR.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2")

Often then manual repairs are better than the auto repair, plus you have control over which repairs. Sometimes chkdsk & fixboot depend on each other (maybe why the auto repair has to run multiple times?).

How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
# is comment do not copy or type comments
BootRec.exe /fixMBR   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r  #(have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector or see bootsect.exe commands
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
Use bootsect.exe to repair XP & older or Vista/7 bootsectors - Use diskpart, then list volumes to see which drive to use 
bootsect.exe /nt52 c:  *compatible* with operating systems older (XP) than Windows Vista.
bootsect.exe /nt60 c:  *compatible* with Windows Vista, Windows Server 2008 or later

---

### Post by Mark201 on 2011-12-27
I think I followed all the instructions. The only thing is that it said that the recovered Windows thing was on the D drive according to the windows repair screen. Anyway I ran chkdsk on both C and D, and the other instructions too. When I restarted the laptop I got a screen saying "BOOTMGR is missing. Press any key to restart" When I press any key it eventually brings up a screen saying
"Non-system disk or disk error
Replace and strike any key when ready"

If I hit any key there, it just brings me back to the BOOTMGR error

---

### Post by Mark201 on 2011-12-27
I tried to follow these instructions 

 [http://www.howtogeek.com/howto/windows-vista/fixing-bootmgr-is-missing-error-while-trying-to-boot-windows-vista/](http://www.howtogeek.com/howto/windows-vista/fixing-bootmgr-is-missing-error-while-trying-to-boot-windows-vista/)

But when I select the OS and click next, I get the error "This version of System Recovery Options is not compatible with the version of Windows you are trying to repair. Try using a recovery disc that is compatible with this version of Windows"..

---

### Post by Mark201 on 2011-12-27
I tried to follow these instructions 

 [http://www.howtogeek.com/howto/windows-vista/fixing-bootmgr-is-missing-error-while-trying-to-boot-windows-vista/](http://www.howtogeek.com/howto/windows-vista/fixing-bootmgr-is-missing-error-while-trying-to-boot-windows-vista/)

But when I select the OS and click next, I get the error "This version of System Recovery Options is not compatible with the version of Windows you are trying to repair. Try using a recovery disc that is compatible with this version of Windows"..

Tbh I think I'm just at the stage where I'm willing to just reinstall Windows and get it over with. Is this as simple as just sticking in the install CD and following the instructions?

Gparted now says that all of the disk is 'inallocated' but testdisk is still showing the same partitions as I posted before.

---

### Post by oldfred on 2011-12-27
Do you have the same version of Windows?

Did you move boot flag to Windows partition as that will then think it is the wrong version?

It will not reinstall unless you have the boot flag on the NTFS partition anyway.

---

### Post by Mark201 on 2011-12-27
> **oldfred said:**
> Do you have the same version of Windows?

Did you move boot flag to Windows partition as that will then think it is the wrong version?

It will not reinstall unless you have the boot flag on the NTFS partition anyway.

I think I may have forgotten to do that. How is it done? I would have thought it could be done through gparted, but as said gparted is only showing one block of unallocated space. Nothing else.

---

### Post by Mark201 on 2011-12-27
When I highlight the partition in gparted, it says under Device Information that the Partition Table is unrecognised. Can it be done in testdisk, since that seems to recognise my partitions properly

---

### Post by Mark201 on 2011-12-27
Ok I figured out how to set a partition as bootable on testdisk (set it to have an astrix?) I think I've set it on the right one (the only NTFS, but it was only 10gb..) so I've put in the windows USB and running an automatic recovery on that. We will see how it goes..

---

### Post by oldfred on 2011-12-27
If gparted is not showing partitions that is saying some partition has corruption of some sort. I had gparted not even show my XP drive even though I could boot XP. I ran chkdsk on the NTFS partition and then gparted worked. (XP booted a bit faster also.)

I might run chkdsk on all NTFS partitions and/or e2fsck on ext4 or ext3 partitions.

You can set boot flag with Disk Utility or from command line. Does Disk Utility show partitions correctly?

#set boot flag on for sda2 (off on others)
sudo sfdisk -A2 /dev/sda
#or:
parted /dev/sda set 2 boot on

In Windows command line you set the active partition. Not sure of exact command anymore.

---

### Post by Mark201 on 2011-12-27
How do I run Disk Utility? A quick google implies that its a Mac thing

---

### Post by Mark Phelps on 2011-12-27
Use Dash.  Click on the icon on the upper left corner of the screen, enter Disk, it will show an icon for Disk Utility.  Just click it to launch it.

---

### Post by Mark201 on 2011-12-27
Which screen is this that you're referring to?

---

### Post by Mark201 on 2011-12-27
Apologies, found it. It recognised them. Screenshot on the way. If its at all possible to just wipe everything so I can reinstall Windows please let me know. I just need to be able to boot up windows on this ASAP

---

### Post by Mark201 on 2011-12-27
Screenshot:
 
[IMG]http://i54.tinypic.com/oi5cie.jpg[/IMG]
 
I'm really lost at the moment (not that I wasn't before).
 
I think the DIABLO_D 1.0 GB FAT is where the Windows bootloader originally was (?), it was NTFS but then at some stage just decided to change to FAT 32.
 
Also note the last 'partition' has TB at the end... so clearly there's some corruption somewhere.
 
 
Edit - Actually the NTFS is the only one with the bootable flag according to Disk Utility....
Here is a screenshot from testdisk after a 'quick search' (which, ironically, took about half an hour):
[IMG]http://i56.tinypic.com/e97qqf.jpg[/IMG]
 
Should the NTFS be set to the boot flag? I think I set the boot flag on it before and had a problem so put it back. Can't remember what the problem was though.
 
This is now the screen I get when I turn on my laptop:
 
[IMG]http://i51.tinypic.com/2ecdy4i.jpg[/IMG]

---

### Post by Mark201 on 2011-12-27
Just on this...
 
> **oldfred said:**
> Do you have the same version of Windows?

 
Is it possible it's complaining because I have W7 professional with SP1 on my USB? Instead of just W7 professional?

---

### Post by oldfred on 2011-12-27
I quickly looked that error up in google but could not find anything definitive. You should check and see if anything does relate to your issues.

How can you have a mismatch of versions? If you have copied a different file that would be a mismatch. But normal Windows repairs do not replace winload.exe as that is just part of the main Windows install. Without that file you do not have an install.

In Ubuntu there is a screenshot application, it would be much clearer than your camera shots.


Post this so we can see what is where.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

---

### Post by Mark201 on 2011-12-28
Results.txt:
 
```
                  Boot Info Script 0.60    from 17 May 2011
 
 
============================= Boot Info Summary: ===============================
 
 => Windows is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.
 => MS-DOS 3.30 through Windows 95 (A) is installed in the MBR of /dev/sdc.
 
sda1: __________________________________________________________________________
 
    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot.ini /boot/bcd /KERNEL.SYS /COMMAND.COM
 
sda2: __________________________________________________________________________
 
    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe
 
sda3: __________________________________________________________________________
 
    File system:       ext2
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
 
sdb1: __________________________________________________________________________
 
    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Mounting failed:   fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
 
sdc1: __________________________________________________________________________
 
    File system:       vfat
    Boot sector type:  FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        
 
============================ Drive/Partition Info: =============================
 
Drive: sda _____________________________________________________________________
 
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
 
Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
 
/dev/sda1         160,000,000   162,047,999     2,048,000   c W95 FAT32 (LBA)
/dev/sda2    *    163,999,744   202,736,367    38,736,624   7 NTFS / exFAT / HPFS
/dev/sda3         343,730,176   613,629,951   269,899,776  83 Linux
/dev/sda4         613,629,954   625,153,409    11,523,456   f W95 Extended (LBA)
/dev/sda5         613,632,000   625,141,743    11,509,744  82 Linux swap / Solaris
 
/dev/sda4 ends after the last sector of /dev/sda
 
Drive: sdb _____________________________________________________________________
 
Disk /dev/sdb: 8006 MB, 8006926336 bytes
16 heads, 32 sectors/track, 30544 cylinders, total 15638528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
 
Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
 
/dev/sdb1    *          8,064    15,638,527    15,630,464   7 NTFS / exFAT / HPFS
 
 
Drive: sdc _____________________________________________________________________
 
Disk /dev/sdc: 1993 MB, 1993342976 bytes
2 heads, 63 sectors/track, 30898 cylinders, total 3893248 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
 
Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
 
/dev/sdc1    *             32     3,893,247     3,893,216   6 FAT16
 
 
"blkid" output: ________________________________________________________________
 
Device           UUID                                   TYPE       LABEL
 
/dev/loop0                                              squashfs   
/dev/sda1        3B20-5946                              vfat       DIABLO_D
/dev/sda2        640A7BD30A7BA12A                       ntfs       
/dev/sda3        122d748a-e02c-4bc0-a25b-4e7ae0814a1a   ext2       New Volume
/dev/sda5        85f984a9-3eff-41c8-83d1-0af5d11df44e   swap       
/dev/sdb1        2E5CCE515CCE138D                       ntfs       
/dev/sdc1        4092-4670                              vfat       MARK CISCO
 
================================ Mount points: =================================
 
Device           Mount_Point              Type       Options
 
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/MARK CISCO        vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
 
 
================================ sda1/boot.ini: ================================
 
--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
D:\Avldr.bin="Avlgo - EFIBOOT_quick.img" 
--------------------------------------------------------------------------------
 
======================== Unknown MBRs/Boot Sectors/etc: ========================
 
Unknown BootLoader on sda1
 
00000000  eb 58 90 46 72 65 65 44  4f 53 20 00 02 08 26 00  |.X.FreeDOS ...&.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 68 89 09  |........?....h..|
00000020  00 40 1f 00 cd 07 00 00  00 00 00 00 02 00 00 00  |.@..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 46 59 20 3b 4e  4f 20 4e 41 4d 45 20 20  |..)FY ;NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 41  |{......|.N..V@.A|
00000070  bb aa 55 cd 13 72 10 81  fb 55 aa 75 0a f6 c1 01  |..U..r...U.u....|
00000080  74 05 fe 46 02 eb 2d 8a  56 40 b4 08 cd 13 73 05  |t..F..-.V@....s.|
00000090  b9 ff ff 8a f1 66 0f b6  c6 40 66 0f b6 d1 80 e2  |.....f...@f.....|
000000a0  3f f7 e2 86 cd c0 ed 06  41 66 0f b7 c9 66 f7 e1  |?.......Af...f..|
000000b0  66 89 46 f8 83 7e 16 00  75 38 83 7e 2a 00 77 32  |f.F..~..u8.~*.w2|
000000c0  66 8b 46 1c 66 83 c0 0c  bb 00 80 b9 01 00 e8 2b  |f.F.f..........+|
000000d0  00 e9 2c 03 a0 fa 7d b4  7d 8b f0 ac 84 c0 74 17  |..,...}.}.....t.|
000000e0  3c ff 74 09 b4 0e bb 07  00 cd 10 eb ee a0 fb 7d  |<.t............}|
000000f0  eb e5 a0 f9 7d eb e0 98  cd 16 cd 19 66 60 80 7e  |....}.......f`.~|
00000100  02 00 0f 84 20 00 66 6a  00 66 50 06 53 66 68 10  |.... .fj.fP.Sfh.|
00000110  00 01 00 b4 42 8a 56 40  8b f4 cd 13 66 58 66 58  |....B.V@....fXfX|
00000120  66 58 66 58 eb 33 66 3b  46 f8 72 03 f9 eb 2a 66  |fXfX.3f;F.r...*f|
00000130  33 d2 66 0f b7 4e 18 66  f7 f1 fe c2 8a ca 66 8b  |3.f..N.f......f.|
00000140  d0 66 c1 ea 10 f7 76 1a  86 d6 8a 56 40 8a e8 c0  |.f....v....V@...|
00000150  e4 06 0a cc b8 01 02 cd  13 66 61 0f 82 75 ff 81  |.........fa..u..|
00000160  c3 00 02 66 40 49 75 94  c3 42 4f 4f 54 4d 47 52  |...f@Iu..BOOTMGR|
00000170  20 20 20 20 00 00 00 00  00 00 00 00 00 00 00 00  |    ............|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 42 4f  |..............BO|
000001b0  4f 54 4d 47 52 20 69 73  20 6d 69 73 73 69 6e 67  |OTMGR is missing|
000001c0  ff 0d 0a 44 69 73 6b 20  65 72 72 6f 72 ff 0d 0a  |...Disk error...|
000001d0  50 72 65 73 73 20 61 6e  79 20 6b 65 79 20 74 6f  |Press any key to|
000001e0  20 72 65 73 74 61 72 74  0d 0a 00 00 00 00 00 00  | restart........|
000001f0  00 00 00 00 00 00 00 00  00 ac c1 ce 00 00 55 aa  |..............U.|
00000200
 
Unknown BootLoader on sda4
 
00000000  35 73 34 95 d3 86 78 74  21 16 c7 3c 81 47 10 b1  |5s4...xt!..<.G..|
00000010  3a 67 0f 3d 97 8e d1 25  19 91 30 4a 1f 9d cd 09  |:g.=...%..0J....|
00000020  78 55 fa e8 93 56 ab ad  f9 ab 45 ed 8e 75 47 b0  |xU...V....E..uG.|
00000030  56 f6 9d 72 50 61 97 f4  2a cb 47 88 f1 b8 9e 16  |V..rPa..*.G.....|
00000040  3e 29 38 f3 51 14 9c 6e  6f 10 a3 27 f0 16 3b 45  |>)8.Q..no..'..;E|
00000050  18 11 82 c7 18 45 4c d1  a6 ba 47 fd 9a b3 69 13  |.....EL...G...i.|
00000060  d9 33 a3 b5 3b 5d af d8  69 cf 7b a7 01 23 31 27  |.3..;]..i.{..#1'|
00000070  e1 3b 0e 38 a9 99 9f 99  5d c3 99 8e 06 f9 1c 33  |.;.8....]......3|
00000080  d0 04 72 08 6e de 41 13  d0 23 60 65 15 9e ec c1  |..r.n.A..#`e....|
00000090  53 29 a7 43 7f d5 4b 9b  e9 12 0b b1 8a 1c 6e 2d  |S).C..K.......n-|
000000a0  5c d4 e8 21 3b b6 4c 52  8b 89 da 7c 56 9a 54 3c  |\..!;.LR...|V.T<|
000000b0  d5 06 31 0a 42 44 b6 ec  3f cb f0 1c 68 9b c2 5f  |..1.BD..?...h.._|
000000c0  7e e8 17 8a ae f1 6c 90  7f 21 e5 26 9a 4e f4 17  |~.....l..!.&.N..|
000000d0  4e 17 28 fa d1 5f be dd  a0 65 4d 81 03 7d 82 88  |N.(.._...eM..}..|
000000e0  46 09 25 14 08 ea 58 55  f6 f0 e2 87 b3 1d aa 22  |F.%...XU......."|
000000f0  45 8f cf 2d a0 8e 2d 2a  4a e3 48 52 b4 b6 e1 a6  |E..-..-*J.HR....|
00000100  8a c7 d1 81 7c a3 26 1a  42 1b 60 a9 e3 a1 ec 33  |....|.&.B.`....3|
00000110  04 12 86 2c b3 6d 87 81  7c 36 91 6f 66 06 d4 4d  |...,.m..|6.of..M|
00000120  0c 22 44 7b 22 3d cf 20  ba 59 91 ec 8e 06 eb cd  |."D{"=. .Y......|
00000130  78 4c 16 35 5a 90 c1 03  da ba e4 c4 08 8f de b2  |xL.5Z...........|
00000140  04 3f 55 68 92 f7 e3 96  bc 43 4c e0 0a 57 9e 25  |.?Uh.....CL..W.%|
00000150  f5 14 a2 10 f0 a0 a5 a9  22 42 02 27 24 b6 a3 21  |........"B.'$..!|
00000160  f9 af bf 66 4b 49 c5 cb  05 a1 75 31 90 82 27 20  |...fKI....u1..' |
00000170  0c 2e a1 4b 32 4e c0 2e  8a 42 8e a8 42 a8 54 91  |...K2N...B..B.T.|
00000180  74 8f 50 21 ab 54 04 e9  8a 22 7a 86 06 e1 a2 ae  |t.P!.T..."z.....|
00000190  9c 1b 6e 10 11 f5 c1 f9  f5 06 2f 55 10 8a b5 6f  |..n......./U...o|
000001a0  b7 93 09 41 5d 09 5e 49  b1 10 b5 75 57 a7 9d 64  |...A].^I...uW..d|
000001b0  77 5b 66 ea fa a2 1f 24  e9 e7 99 71 ed 83 00 fe  |w[f....$...q....|
000001c0  ff ff 82 fe ff ff fe 07  00 00 f0 9f af 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
 
 

```
 
I've updated the Disk Utility picture above with a clearer screenshot

---

### Post by oldfred on 2011-12-28
You show no Linux installed now at all and a large ext2 partition. Better to use ext4 or ext3.

As far as script goes it shows Windows correctly. You have Windows boot loader and all the correct files and boot flag in sda2. Can you hit f8 and get into a repair console on booting? But if some files are wrong version I do not know.

How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

---

