---
title: "Clean install, can I mess up GRUB?"
date: 2010-06-12
forum: General Help
---

### Post by RJ12 on 2010-06-12
Ok, so I have been testing Ubuntu 10.04 for a while. I hate upgrades, so I want to do a clean install. I installed GRUB into the partition of Ubuntu (Not the MBR) and got EasyBCD to redirect to it, if I install the new version of Ubuntu (wiping out the old one which is 9.10) will it mess up everything the same way it would if I didn't have GRUB in a partition, and on the MBR?

---

### Post by wilee-nilee on 2010-06-12
> **RJ12 said:**
> Ok, so I have been testing Ubuntu 10.04 for a while. I hate upgrades, so I want to do a clean install. I installed GRUB into the partition of Ubuntu (Not the MBR) and got EasyBCD to redirect to it, if I install the new version of Ubuntu (wiping out the old one which is 9.10) will it mess up everything the same way it would if I didn't have GRUB in a partition, and on the MBR?

I think without any description the type of ext used that esybcd could read, and knowing that easybcd2 has been gotten to work with grub2 by a few people, the ext4 of Lucid may be a problem.

Most of us are grubcentric, it is much easier to reload and manipulate, personally I think using easybcd is a problem just waiting to happen when grub will do the work if installed correctly.

Putting grub into a partition is for somebody who knows enough already and wouldn't need to even use this forum but to help others, do you get what I'm saying, your over your head here probably, but hey who's not.;)

You seem spooked by grub like many MS users are.

---

### Post by RJ12 on 2010-06-12
Well, I'm just paranoid that GRUB2 won't let me boot into Windows 7, but I guess I can worry less (the GRUB I have, when I click Ubuntu on the Windows Boot Loader, can see it, but I haven't tested it), do you think 10.04 will be the same?

---

### Post by wilee-nilee on 2010-06-12
> **RJ12 said:**
> Well, I'm just paranoid that GRUB2 won't let me boot into Windows 7, but I guess I can worry less (the GRUB I have, when I click Ubuntu on the Windows Boot Loader, can see it, but I haven't tested it), do you think 10.04 will be the same?

The main problem with grub, any type is that people install it into a windows partition when it goes to the mbr. which would be sda if you have only one HD generally not sdX X=partition numbers.
 
We can get you setup quite easily if you understand.

I would also say your smart to ask some questions to avoid problems and get a grasp of the process.;)

---

### Post by RJ12 on 2010-06-12
> **wilee-nilee said:**
> The main problem with grub, any type is that people install it into a windows partition when it goes to the mbr. which would be sda if you have only one HD generally not sdX X=partition numbers.
 
We can get you setup quite easily if you understand.

I would also say your smart to ask some questions to avoid problems and get a grasp of the process.;)


So, is there a special way to install 10.04 then? Also thanks for the comment about me being smart, it's well appreciated! :p

---

### Post by wilee-nilee on 2010-06-12
> **RJ12 said:**
> So, is there a special way to install 10.04 then? Also thanks for the comment about me being smart, it's well appreciated! :p

So it helps to know how many hard drives you have, also if your using a dell computer which has a data safe program that causes problems, and what your set up is now. So click on the link in my sig and post it even though you have no boot problems it will answer some key points to consider. 

Always being prepared, is a indicator of a working cognitive process.;)

---

### Post by RJ12 on 2010-06-12
I do not have a dell laptop, I have one hard drive. My laptop is a Toshiba L455D-S5976. The results of the boot info is attached in the ```
 Tags (is that the correct way to post it?)


[CODE]                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

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
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 417571350 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sda and 
                       looks on partition #5 for /boot/grub.
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5888e11a

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2           3,074,048   409,948,159   406,874,112   7 HPFS/NTFS
/dev/sda3         471,437,312   488,396,799    16,959,488  17 Hidden HPFS/NTFS
/dev/sda4         409,962,735   471,427,424    61,464,690   5 Extended
/dev/sda5         409,962,798   464,680,124    54,717,327  83 Linux
/dev/sda6         464,680,188   471,427,424     6,747,237  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        F27AE9B17AE97331                       ntfs       System                        
/dev/sda2        6A500F5F500F30FD                       ntfs       TI103196W0D                   
/dev/sda3        C88ED2BD8ED2A2EC                       ntfs       HDDRECOVERY                   
/dev/sda5        7623a48d-e3cf-40f0-aaed-a0c039b77b6b   ext4                                     
/dev/sda6        71c99141-ca0f-4d63-8a88-7015ad648464   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set 7623a48d-e3cf-40f0-aaed-a0c039b77b6b
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 7623a48d-e3cf-40f0-aaed-a0c039b77b6b
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=7623a48d-e3cf-40f0-aaed-a0c039b77b6b ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 7623a48d-e3cf-40f0-aaed-a0c039b77b6b
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=7623a48d-e3cf-40f0-aaed-a0c039b77b6b ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set f27ae9b17ae97331
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 6a500f5f500f30fd
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
	insmod ntfs
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set c88ed2bd8ed2a2ec
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=7623a48d-e3cf-40f0-aaed-a0c039b77b6b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=71c99141-ca0f-4d63-8a88-7015ad648464 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 213.7GB: boot/grub/core.img
 213.7GB: boot/grub/grub.cfg
 210.9GB: boot/initrd.img-2.6.31-14-generic
 210.5GB: boot/vmlinuz-2.6.31-14-generic
 210.9GB: initrd.img
 210.5GB: vmlinuz
```

---

### Post by llawwehttam on 2010-06-12
> **RJ12 said:**
> Well, I'm just paranoid that GRUB2 won't let me boot into Windows 7

pfffffft. Sorry but I've been telling people how to fix problems in mbr's caused by windows 7 for the last half hour on another forum. Grub is easier to fix and modify than the windows bootloader.

Don't worry, even if you do mess it up (unlikely) this forum is always here to help.

---

### Post by wilee-nilee on 2010-06-12
> **llawwehttam said:**
> pfffffft. Sorry but I've been telling people how to fix problems in mbr's caused by windows 7 for the last half hour on another forum. Grub is easier to fix and modify than the windows bootloader.

Don't worry, even if you do mess it up (unlikely) this forum is always here to help.

I think I know the forum your referencing, it is a pointless task to try to help, but there are some great tutorials there.;)

First I am impressed that you have gotten easybcd the 2 beta version working that is a feat many have not been able to do. Lets, let the more knowledgeable look at the script to see the best approach, I'm just not familiar with easybcd.

---

### Post by RJ12 on 2010-06-12
> **wilee-nilee said:**
> I think I know the forum your referencing, it is a pointless task to try to help, but there are some great tutorials there.;)

First I am impressed that you have gotten easybcd the 2 beta version working that is a feat many have not been able to do. Lets, let the more knowledgeable look at the script to see the best approach, I'm just not familiar with easybcd.
:-o I usually know how to work stuff because of others! I guess this time, it was trial and error

---

### Post by jmstern on 2010-06-12
I was tinkering - attempting to expand the space allocated for /home - and in the process, messed up something.  After several unsuccessful reboots, getting grub error 25, sometimes 22 - realized I had changed the BIOS, to change the boot order sequence from on HD to another... and that caused my issue.

After setting BIOS back to the original order, Ubuntu works.

---

### Post by wilee-nilee on 2010-06-12
> **jmstern said:**
> I was tinkering - attempting to expand the space allocated for /home - and in the process, messed up something.  After several unsuccessful reboots, getting grub error 25, sometimes 22 - realized I had changed the BIOS, to change the boot order sequence from on HD to another... and that caused my issue.

After setting BIOS back to the original order, Ubuntu works.

Cool story bro,:rolleyes: but has no relevance to this thread

---

