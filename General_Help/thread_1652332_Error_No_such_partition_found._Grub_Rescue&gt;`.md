---
title: "Error: No such partition found. Grub Rescue&gt;`"
date: 2010-12-24
forum: General Help
---

### Post by genoboss on 2010-12-24
iight, so i installed Linux  Mint 10 and i deleted my windows partition  by accident, and it became unallocated space. so i did a testdisk and i  figured i had restored the partition because the table looked different  then it was before.

I rebooted my pc and it says partition not found and get a grub rescue but nothing i type works.
So i cannot get into windows or linux. I have Linux mint 10 on a flash drive

So  when i booted into that and went into terminal i typed sudo fdisk -l  and saw sda1 and sda2 (which is suppose to be my windows partition)

i was then told to type find /grub/stage1 but i get the error 15: file not found

```

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5a23c748

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1828    14680064    7  HPFS/NTFS
/dev/sda2   *        1828       38914   297889792    7  HPFS/NTFS

Disk /dev/sdc: 4009 MB, 4009230336 bytes
16 heads, 32 sectors/track, 15294 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       15294     3915248    b  W95 FAT32
```

---

### Post by dandnsmith on 2010-12-24
If you can get to it, get the boot info script from [this site](http://sourceforge.net/projects/bootinfoscript/)
and run it, and then post the results.
This will show the results, and (we hope) provide enough information to enable resuscitation.

It sounds like the partition UUID hasn't been restored (possibly amongst other things.

---

### Post by genoboss on 2010-12-24
I dont know how to instal that file you gave me. im on linux mint live 

```
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 320 GB / 298 GiB - CHS 38914 255 63
     Partition               Start        End    Size in sectors
* HPFS - NTFS              0  32 33  1827 181 18   29360128 [PQSERVICE]
D HPFS - NTFS           1827 181 19 38913  70  5  595779584 [OS]
D Linux                 1827 213 51  5562 141 19   59998208
D Linux                 3674  73 48  7409   1 16   59998208
D Linux                 3679 196 38  7414 124  6   59998208
D Linux                 3682 211 50  7417 139 18   59998208
D Linux Swap            5562 173 52  7386  47  5   29294576
```

this is what i got when i did a deep scan of my lost partitions

---

### Post by dandnsmith on 2010-12-25
On that page I linked to, just above that large Download button, there is a link to 'instructions for use'

HTH

---

### Post by Rubi1200 on 2010-12-25
Definitely agree with dandnsmith that we need to see the results of the script to advise you further.

You can run it from a LM LiveCD or any LiveCD for that matter.

---

### Post by dino99 on 2010-12-25
[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by genoboss on 2010-12-25
```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    29,362,175    29,360,128   7 HPFS/NTFS
/dev/sda2    *     29,362,176   625,141,759   595,779,584   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4009 MB, 4009230336 bytes
16 heads, 32 sectors/track, 15294 cylinders, total 7830528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32     7,830,527     7,830,496   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       135c1469-797f-6241-8db5-85c03c9dd6c4   ext2                                     
/dev/sda1        D01A099C1A0980A8                       ntfs       PQSERVICE                     
/dev/sda2        7C444289444245DC                       ntfs       OS                            
/dev/sda: PTTYPE="dos" 
/dev/sdb1        AED6-E194                              vfat       MALCOMDRIVE                   
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/OS                fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda1        /media/PQSERVICE         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=================== sda2: Location of files loaded by Grub: ===================


    ??GB: boot/grub/stage2

=========================== sdb1/boot/grub/grub.cfg: ===========================


if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Start Linux Mint" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/mint.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Start Linux Mint (compatibility mode)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/mint.seed xforcevesa boot=casper noapic noapci nosplash irqpoll --
    initrd    /casper/initrd.lz
}
menuentry "Check the integrity of the CD" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}

=================== sdb1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/grub.cfg
=======Devices which don't seem to have a corresponding hard drive==============

sdc 
```

---

### Post by genoboss on 2010-12-25
Heres the script of all the information you asked

---

### Post by genoboss on 2010-12-25
i tried to use pqservice to restore my windows or reinstall ubuntu to atleast get a boot loader

---

### Post by oldfred on 2010-12-25
It looks like your only other windows partition was sda2 OS and you overwrote it with the linux install as it also starts at 1827. Did you try to recover this second NTFS partition. It would replace all your linux partitions, but may not boot if you did have linux overwrite parts of it. But you may be able to recover some data, or use photorec to recover files.

D HPFS - NTFS           [COLOR=Red]1827[/COLOR] 181 19 38913  70  5  595779584 [OS]
D Linux                 [COLOR=Red]1827[/COLOR] 213 51  5562 141 19   59998208

---

### Post by genoboss on 2010-12-25
Yes this is what happend. I could not resize my sda2 partition so i tried to do something and accidently deleted it. it became unallocated space. so i used that unallocated space to make a new linux partition which i installed linux on. when i booted. i NOTICED IN THE BOOT MENU or loader it said just linux. I got scared so i used testdisk on linux to restore to original partition table.


this is when i got the grub error.

---

### Post by oldfred on 2010-12-25
Grub in the MBR just links to the rest of the grub files & boot code in the linux partition. If you delete linux partition grub has nowhere to go.

The same with windows. The windows boot loader in the MBR, just looks for the active partition (boot flag) and jumps to the code in the partition boot sector that loads the windows files.

If you overwrote part of the windows install, you may or may not be able to start booting windows but probably overwrote some windows files and it will not boot. You may be able to run some repairs and see data files, but even that may not be recoverable depending on what was overwritten.

Photorec will scan drive for files:
Testdisk & photorec
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://www.linux.com/archive/feed/56588](http://www.linux.com/archive/feed/56588)
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)

---

### Post by genoboss on 2010-12-26
Yea i shouldent have created a partition and installed linux from the windows unallocated space. thats maybe what overwritten some data. But i never formatted, im sure theres some way i can get my windows and data back.

---

### Post by genoboss on 2010-12-26
hOW DO I use photorec. how do i create a partition to send the recovery files to?

---

### Post by oldfred on 2010-12-26
You need to have another drive. Writing to the same drive will just cause more errors.

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

I just created a new partition on another drive and let photorec copy everything into it. It found lots of data and I only had two folders that I had lost. One text files I have saved many times it found all the copies. Not sure I ever found original, but between backup and bits from several of the recovered version I got most of that file back.

Nov 5,2010
5742 files saved in /home/fred/recover/recup_dir directory.
Recovery completed.
txt: 2552 recovered
png: 980 recovered
tx?: 675 recovered
flac: 509 recovered
jpg: 285 recovered
mp3: 138 recovered
gz: 109 recovered
elf: 99 recovered
zip: 85 recovered
ogg: 82 recovered
others: 228 recovered

---

### Post by genoboss on 2010-12-26
i dont have another drive. only 1 hard drive in this laptop

they said i can make a recovery partition

---

### Post by genoboss on 2010-12-26
................bump

---

### Post by genoboss on 2010-12-26
................bump

---

### Post by oldfred on 2010-12-26
Two of the links and everything else I have read say you must copy to another drive unless you have created an image (in another backup). As any more writing to drive will cause even more problems.

How important is data?  When was last backup? It it is not that important then you can just do whatever adn you may get something.

---

### Post by genoboss on 2010-12-27
not that important. but i still want to get it bak. its not something i cant get back though.

plus i dont have a OS. im talkin to you using LINUX UBUNTU MINT LIVE USB 

I have os using USB....

---

### Post by genoboss on 2010-12-27
......................

---

### Post by oldfred on 2010-12-27
I am not sure what you want? IF testdisk cannot recover partition and your overwrote your windows data with linux there is not much you can do except photorec.

Someone else may have other software beside testdisk but I do not know if it would work any better?

---

### Post by genoboss on 2010-12-27
How do i use photorec if i dont have another hard drive

---

### Post by oldfred on 2010-12-27
I do not think you can.

Did you try recovering the NTFS os partition that testdisk found - see post #10?

---

### Post by genoboss on 2010-12-28
Yeah but i dont see all my files. I just see windows recovery and boot mgr.

---

### Post by oldfred on 2010-12-28
Was that just the windows 100MB boot partition and you have another larger system partition? Did testdisk only see that one?

---

### Post by genoboss on 2010-12-28
Yeah when i deleted the windows partition it became unallocated space then when i made a partition out of it for linux i guess it overwritten some data.

but testdisk detected it but it only shows me the boot files (i guess)

---

### Post by genoboss on 2010-12-31
Any advice?.

---

### Post by oldfred on 2010-12-31
Since this thread is titled as about boot issues & grub rescue, you may do better with a new thread on recovery of data. 

I do not have anything more to suggest on  how to recover data if you do not have another drive or way to copy data elsewhere. It sounds like you need another drive or some way to back up data anyway.

---

