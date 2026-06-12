---
title: "Error: file not found. grub rescue (Ubuntu 10.04)"
date: 2011-09-13
forum: General Help
---

### Post by wthelpp on 2011-09-13
Ok so I have a broken eeepc 1000h with no internal HDD. I installed ubuntu 10.04 on my 500 gb external usb hdd and I get the error "Error: file not found ... grub rescue>" 

How do I solve this problem ?

Thanks for your time.

---

### Post by raja.genupula on 2011-09-13
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

in that look for grub rescue

---

### Post by wthelpp on 2011-09-13
Hey raja, thanks for your help. Anychance you can simplify that for me. I am a ubuntu n00b and the link you just provided me with gave me a heart attack :(

---

### Post by raja.genupula on 2011-09-13
ok insert your live cd 
go for live session 
in terminal 
type as ```
sudo os-prober
``` 
give me the output here

---

### Post by wthelpp on 2011-09-13
Ok so I reinstalled ubuntu on a 100gb partition on my 500 gb fat32 external usb hdd.

I get the error "Error: partition not found"

I did what you said connected my hdd and ran terminal on my live usb installation and i get this :

**/dev/sdb5:Ubuntu 10.04.2 LTS (10.04):Ubuntu:linux**

---

### Post by drs305 on 2011-09-13
We can take a look at the status of your boot files if you can boot a LiveCD and run the boot info script. This will generate a RESULTS.txt file. Post the contents of this file and we might be able to see the problem.

Click the "BIS" link in my signature line to take you to the Boot Info Script site.

---

### Post by wthelpp on 2011-09-13
I am using a netbook so I don't have a cd drive.

I do however have the live "cd" installation files on my installation usb.

Please tell me the process and I shall do it.

I must mention that I am an absolute beginner to ubuntu, so I appreciate your patience and knowledge.

---

### Post by drs305 on 2011-09-13
However you can boot to the Desktop. You should be able to do that the same way you installed Ubuntu initially (choose 'Try Ubuntu' if given the option).

The instructions on how to extract and run the script are on the linked page.

Any time you get stuck or don't understand, just ask the question. We were all new to Ubuntu and Linux at some point.

---

### Post by wthelpp on 2011-09-13
Ok I did it.

I pasted the results.txt here: [http://pastebin.com/63AhMp1d](http://pastebin.com/63AhMp1d)

Note: Added here by moderator.
```

                      Boot Info Script 0.60    from 17 May 2011
     
     
    ============================= Boot Info Summary: ===============================
     
     => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sda.
     => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector
        1 of the same hard drive for core.img. core.img is at this location and
        looks in partition 5 for /boot/grub.
     
    sda1: __________________________________________________________________________
     
        File system:       vfat
        Boot sector type:  SYSLINUX 3.86 2010-04-01
        Boot sector info:   Syslinux looks at sector 31116 of /dev/sda1 for its
                           second stage. No errors found in the Boot Parameter
                           Block.
        Operating System:  
        Boot files:        /syslinux/syslinux.cfg /ldlinux.sys
     
    sdb1: __________________________________________________________________________
     
        File system:       vfat
        Boot sector type:  Unknown
        Boot sector info:   No errors found in the Boot Parameter Block.
        Operating System:  
        Boot files:        
     
    sdb2: __________________________________________________________________________
     
        File system:       Extended Partition
        Boot sector type:  -
        Boot sector info:  
     
    sdb5: __________________________________________________________________________
     
        File system:       ext4
        Boot sector type:  -
        Boot sector info:  
        Operating System:  Ubuntu 10.04.2 LTS
        Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
     
    sdb6: __________________________________________________________________________
     
        File system:       swap
        Boot sector type:  -
        Boot sector info:  
     
    ============================ Drive/Partition Info: =============================
     
    Drive: sda _____________________________________________________________________
     
    Disk /dev/sda: 4089 MB, 4089445376 bytes
    255 heads, 63 sectors/track, 497 cylinders, total 7987198 sectors
    Units = sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
     
    Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
     
    /dev/sda1    *              1     7,987,197     7,987,197   c W95 FAT32 (LBA)
     
     
    Drive: sdb _____________________________________________________________________
     
    Disk /dev/sdb: 500.1 GB, 500105740288 bytes
    255 heads, 63 sectors/track, 60801 cylinders, total 976769024 sectors
    Units = sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
     
    Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
     
    /dev/sdb1    *             63   782,123,023   782,122,961   b W95 FAT32
    /dev/sdb2         782,125,054   976,766,975   194,641,922   5 Extended
    /dev/sdb5         782,125,056   970,809,343   188,684,288  83 Linux
    /dev/sdb6         970,811,392   976,766,975     5,955,584  82 Linux swap / Solaris
     
     
    "blkid" output: ________________________________________________________________
     
    Device           UUID                                   TYPE       LABEL
     
    /dev/loop0                                              squashfs  
    /dev/sda1        1DE3-111D                              vfat       PENDRIVE
    /dev/sdb1        40A5-1DED                              vfat       UNTITLED
    /dev/sdb5        6539b009-3f70-4c0a-b890-cb9d59ca2579   ext4      
    /dev/sdb6        8d49c50c-e71f-4690-8610-544fdaf0960f   swap      
     
    ================================ Mount points: =================================
     
    Device           Mount_Point              Type       Options
     
    /dev/loop0       /rofs                    squashfs   (ro,noatime)
    /dev/sda1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
    /dev/sdb1        /media/UNTITLED          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
    /dev/sdb5        /media/6539b009-3f70-4c0a-b890-cb9d59ca2579 ext4       (rw,nosuid,nodev,uhelper=udisks)
     
     
    ========================= sda1/syslinux/syslinux.cfg: ==========================
     
    --------------------------------------------------------------------------------
    include menu.cfg
    default vesamenu.c32
    prompt 0
    timeout 50
    gfxboot bootlogo
    --------------------------------------------------------------------------------
     
    ================= sda1: Location of files loaded by Syslinux: ==================
     
               GiB - GB             File                                 Fragment(s)
     
                ?? = ??             ldlinux.sys                                    1
                ?? = ??             syslinux/syslinux.cfg                          1
                ?? = ??             syslinux/vesamenu.c32                          1
     
    ============== sda1: Version of COM32(R) files used by Syslinux: ===============
     
     syslinux/vesamenu.c32              :  COM32R module (v3.xx)
     
    =========================== sdb5/boot/grub/grub.cfg: ===========================
     
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
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 6539b009-3f70-4c0a-b890-cb9d59ca2579
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
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 6539b009-3f70-4c0a-b890-cb9d59ca2579
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
    menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
            recordfail
            insmod ext2
            set root='(hd1,5)'
            search --no-floppy --fs-uuid --set 6539b009-3f70-4c0a-b890-cb9d59ca2579
            linux   /boot/vmlinuz-2.6.32-28-generic root=UUID=6539b009-3f70-4c0a-b890-cb9d59ca2579 ro   quiet splash
            initrd  /boot/initrd.img-2.6.32-28-generic
    }
    menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
            recordfail
            insmod ext2
            set root='(hd1,5)'
            search --no-floppy --fs-uuid --set 6539b009-3f70-4c0a-b890-cb9d59ca2579
            echo    'Loading Linux 2.6.32-28-generic ...'
            linux   /boot/vmlinuz-2.6.32-28-generic root=UUID=6539b009-3f70-4c0a-b890-cb9d59ca2579 ro single
            echo    'Loading initial ramdisk ...'
            initrd  /boot/initrd.img-2.6.32-28-generic
    }
    ### END /etc/grub.d/10_linux ###
     
    ### BEGIN /etc/grub.d/20_memtest86+ ###
    menuentry "Memory test (memtest86+)" {
            insmod ext2
            set root='(hd1,5)'
            search --no-floppy --fs-uuid --set 6539b009-3f70-4c0a-b890-cb9d59ca2579
            linux16 /boot/memtest86+.bin
    }
    menuentry "Memory test (memtest86+, serial console 115200)" {
            insmod ext2
            set root='(hd1,5)'
            search --no-floppy --fs-uuid --set 6539b009-3f70-4c0a-b890-cb9d59ca2579
            linux16 /boot/memtest86+.bin console=ttyS0,115200n8
    }
    ### END /etc/grub.d/20_memtest86+ ###
     
    ### BEGIN /etc/grub.d/30_os-prober ###
    menuentry "Ubuntu, with Linux 2.6.32-33-generic (on /dev/sdc1)" {
            insmod ext2
            set root='(hd2,1)'
            search --no-floppy --fs-uuid --set dd9a6eb0-b575-4d96-81bc-e7db74060436
            linux /boot/vmlinuz-2.6.32-33-generic root=UUID=dd9a6eb0-b575-4d96-81bc-e7db74060436 ro quiet splash
            initrd /boot/initrd.img-2.6.32-33-generic
    }
    menuentry "Ubuntu, with Linux 2.6.32-33-generic (recovery mode) (on /dev/sdc1)" {
            insmod ext2
            set root='(hd2,1)'
            search --no-floppy --fs-uuid --set dd9a6eb0-b575-4d96-81bc-e7db74060436
            linux /boot/vmlinuz-2.6.32-33-generic root=UUID=dd9a6eb0-b575-4d96-81bc-e7db74060436 ro single
            initrd /boot/initrd.img-2.6.32-33-generic
    }
    menuentry "Ubuntu, with Linux 2.6.32-28-generic (on /dev/sdc1)" {
            insmod ext2
            set root='(hd2,1)'
            search --no-floppy --fs-uuid --set dd9a6eb0-b575-4d96-81bc-e7db74060436
            linux /boot/vmlinuz-2.6.32-28-generic root=UUID=dd9a6eb0-b575-4d96-81bc-e7db74060436 ro quiet splash
            initrd /boot/initrd.img-2.6.32-28-generic
    }
    menuentry "Ubuntu, with Linux 2.6.32-28-generic (recovery mode) (on /dev/sdc1)" {
            insmod ext2
            set root='(hd2,1)'
            search --no-floppy --fs-uuid --set dd9a6eb0-b575-4d96-81bc-e7db74060436
            linux /boot/vmlinuz-2.6.32-28-generic root=UUID=dd9a6eb0-b575-4d96-81bc-e7db74060436 ro single
            initrd /boot/initrd.img-2.6.32-28-generic
    }
    ### END /etc/grub.d/30_os-prober ###
     
    ### BEGIN /etc/grub.d/40_custom ###
    # This file provides an easy way to add custom menu entries.  Simply type the
    # menu entries you want to add after this comment.  Be careful not to change
    # the 'exec tail' line above.
    ### END /etc/grub.d/40_custom ###
    --------------------------------------------------------------------------------
     
    =============================== sdb5/etc/fstab: ================================
     
    --------------------------------------------------------------------------------
    # /etc/fstab: static file system information.
    #
    # Use 'blkid -o value -s UUID' to print the universally unique identifier
    # for a device; this may be used with UUID= as a more robust way to name
    # devices that works even if disks are added and removed. See fstab(5).
    #
    # <file system> <mount point>   <type>  <options>       <dump>  <pass>
    proc            /proc           proc    nodev,noexec,nosuid 0       0
    # / was on /dev/sdb5 during installation
    UUID=6539b009-3f70-4c0a-b890-cb9d59ca2579 /               ext4    errors=remount-ro 0       1
    # swap was on /dev/sdb6 during installation
    UUID=8d49c50c-e71f-4690-8610-544fdaf0960f none            swap    sw              0       0
    --------------------------------------------------------------------------------
     
    =================== sdb5: Location of files loaded by Grub: ====================
     
               GiB - GB             File                                 Fragment(s)
     
     423.078907013 = 454.277517312  boot/grub/core.img                             1
     405.146202087 = 435.022422016  boot/grub/grub.cfg                             1
     423.086326599 = 454.285484032  boot/initrd.img-2.6.32-28-generic              1
     423.077507019 = 454.276014080  boot/vmlinuz-2.6.32-28-generic                 1
     423.086326599 = 454.285484032  initrd.img                                     1
     423.077507019 = 454.276014080  vmlinuz                                        1
     
    ======================== Unknown MBRs/Boot Sectors/etc: ========================
     
    Unknown BootLoader on sdb1
     
    00000000  eb 58 90 4d 53 57 49 4e  34 2e 31 00 02 40 5e 00  |.X.MSWIN4.1..@^.|
    00000010  02 00 00 00 00 f8 00 00  20 00 ff 00 3f 00 00 00  |........ ...?...|
    00000020  d1 3f 9e 2e e7 74 01 00  00 00 00 00 eb 02 00 00  |.?...t..........|
    00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
    00000040  80 00 29 ed 1d a5 40 4e  4f 20 4e 41 4d 45 20 20  |..)...@NO NAME  |
    00000050  20 20 46 41 54 33 32 20  20 20 fa 31 c0 8e d0 bc  |  FAT32   .1....|
    00000060  00 7c fb 8e d8 e8 00 00  5e 83 c6 19 bb 07 00 fc  |.|......^.......|
    00000070  ac 84 c0 74 06 b4 0e cd  10 eb f5 30 e4 cd 16 cd  |...t.......0....|
    00000080  19 0d 0a 4e 6f 6e 2d 73  79 73 74 65 6d 20 64 69  |...Non-system di|
    00000090  73 6b 0d 0a 50 72 65 73  73 20 61 6e 79 20 6b 65  |sk..Press any ke|
    000000a0  79 20 74 6f 20 72 65 62  6f 6f 74 0d 0a 00 00 00  |y to reboot.....|
    000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
    *
    000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
    00000200

```

---

### Post by drs305 on 2011-09-13
I can see two possible reasons for the problem.

First, make sure the BIOS is booting your sdb (500GB) drive first. You can check by entering the BIOS setup during boot and making sure the 500GB drive is first in priority. This may be all you have to do. You may also only have to remove the flash drive and reboot, if that has been inserted when you boot (and was inserted when you ran the script).

While you are there, check for the possible second problem. Note the reported size of your Ubuntu drive. See if it reports the drive as only being 137GB. If it does, your BIOS is only capable of reading files within the first 137GB of the drive, and your Ubuntu boot files are currently near the end of the drive (beyond 137GB). There are some things we can do to fix this, but we will wait to see what you report.

---

### Post by wthelpp on 2011-09-13
I once installed ubuntu on my friends 160gb HDD and it worked fine on my netbook. And I made sure the boot priority was for my hdd, I got the same error. No other device was present in my netbook.

"Error: partition not found ... grub rescue>"

---

### Post by drs305 on 2011-09-13
Check the BIOS reported disk size.

You can also check to see if BIOS/GRUB can see the boot files from the Grub rescue prompt, in a roundabout way.

Type the first part of each of these commands (to but not including the # symbol). The info after the # is what you should see on a working system. If you still have another drive connected, the 0 may need to be 1 in the commands.

```

ls # (hd0), (hd0,5)
ls (hd0,5)/  # System folders, and 'vmlinuz' and 'initrd.img'
ls (hd0,5)/boot # a grub folder
ls (hd0,5)/boot/grub # a lot of *.mod files, and if you can find it in the long list, grub.cfg

```

---

### Post by wthelpp on 2011-09-13
Each time I type these I get the error "no such partition"

How do I check the bios reported disk size ?

---

### Post by drs305 on 2011-09-13
> **wthelpp said:**
> Each time I type these I get the error "no such partition"

How do I check the bios reported disk size ?

Did you try (hd**1**,5) as well. You may not have seen my edit.

To find the reported disk size, you enter BIOS setup. The key to press during boot varies by manufacturer. It's usually one of the function keys (F1, F2, etc), the DEL or ESC key. Once in setup, there should be a section that describes the drives (size, id's, etc).

If it is reported as 137GB, see if there is an option in BIOS to enable LBA or large drives so it can see the entire drive.

---

### Post by wthelpp on 2011-09-13
when I type (hd1,5) it tells me : hd1,5 cannot get C/H/S values.

And there is no option to see drive size on my bios. I can only set time, date, boot priority and some other stuff.

BTW in the IDE config. it tells me " Primary IDE master: not detected"

---

### Post by drs305 on 2011-09-13
```
ls (hd1,5)**/**
```
as well as the other ones listed previously, replacing (hd0, with (hd1,

---

### Post by wthelpp on 2011-09-13
Yeah thats what I did 

[B]ls (hd1,5)/

ls (hd1,5)/boot

ls (hd1,5)/boot/grub[/B]

I get the same error *hd1,5 cannot get C/H/S values.*

Any other ideas ?

And thanks for helping me out again, appreciate it.

---

### Post by drs305 on 2011-09-13
I have to log off in a few moments. We haven't really established whether you are having a hard drive/BIOS issue or something else.

I think I'd first try booting to the Desktop (however you did it earlier - LiveUSB?). Once at the Desktop, you can try mounting your Ubuntu partition to see if the files exist. 

Open a terminal Window and mount your Ubuntu partition (it should be sda5 or sdb5). You access the terminal via System, Applications menu or typing 'terminal' in the Dash Window. Or ALT-F2.

```
sudo mount /dev/sdb5 /mnt
gksu nautilus /mnt
```

Once you know whether the system files still exist:
```
sudo umount /mnt
```

If the files are there, I would probably try to shrink the Ubuntu partition using Gparted so the end of it is no farther into the disk than about 130GB.

If that doesn't work, I think it's time to reinstall. Create a partition within the first 130GB of the drive and select the partitions manually.

If you can't read any of the files once you mounted the partition, perhaps it is a disk problem and you should figure out whether the hard drive cables, etc are as they should be.

I understand you don't have much Ubuntu experience and you may not understand how to do the things I've suggested. You can google these forums or ask from others who may read this thread.  I'll check back when I can.

I wrote a Grub Rescue thread, which might provide some additional help:
[http://ubuntuforums.org/showthread.php?t=1594052]("http://ubuntuforums.org/showthread.php?t=1594052")

---

### Post by wthelpp on 2011-09-13
> **drs305 said:**
> I have to log off in a few moments. We haven't really established whether you are having a hard drive/BIOS issue or something else.

I think I'd first try booting to the Desktop (however you did it earlier - LiveUSB?). Once at the Desktop, you can try mounting your Ubuntu partition to see if the files exist. 

Open a terminal Window and mount your Ubuntu partition (it should be sda5 or sdb5). You access the terminal via System, Applications menu or typing 'terminal' in the Dash Window. Or ALT-F2.

```
sudo mount /dev/sdb5 /mnt
gksu nautilus /mnt
```

Once you know whether the system files still exist:
```
sudo umount /mnt
```

If the files are there, I would probably try to shrink the Ubuntu partition using Gparted so the end of it is no farther into the disk than about 130GB.

If that doesn't work, I think it's time to reinstall. Create a partition within the first 130GB of the drive and select the partitions manually.

If you can't read any of the files once you mounted the partition, perhaps it is a disk problem and you should figure out whether the hard drive cables, etc are as they should be.

I understand you don't have much Ubuntu experience and you may not understand how to do the things I've suggested. You can google these forums or ask from others who may read this thread.  I'll check back when I can.

I wrote a Grub Rescue thread, which might provide some additional help:
[http://ubuntuforums.org/showthread.php?t=1594052]("http://ubuntuforums.org/showthread.php?t=1594052")

Gparted Fixed it ...

---

### Post by drs305 on 2011-09-13
Excellent.  :-)  

So you just shrank the partition size?

Edit: Looks like you've already done the following. Thanks.
Once you have no more questions on this issue, please mark the thread SOLVED via the 'Thread Tools' link at the top right of the first post. It's helpful for both helpers and those seeking threads with solutions.

Happy Ubuntu-ing !

---

