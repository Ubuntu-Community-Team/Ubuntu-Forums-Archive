---
title: "Booting Issues"
date: 2010-09-19
forum: General Help
---

### Post by The_Shady_1 on 2010-09-19
I seem to be having some issue with GRUB. I installed the kernel update just last night and when I went to turn on my computer today my entry to Win 7 was gone.I am able to boot into Lucid with ease but what happened to Windows 7 all of a sudden? I was using it just y-day and restarted to boot into Lucid to catch up on any updates. 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x32f932f8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60802   488384512    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x79907b78

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       42804   343823098+   7  HPFS/NTFS
/dev/sdb2           42805       60802   144563201    5  Extended
/dev/sdb5   *       42805       60066   138650624   83  Linux
/dev/sdb6           60066       60802     5911552   82  Linux swap / Solaris

Disk /dev/sdc: 2030 MB, 2030043136 bytes
129 heads, 32 sectors/track, 960 cylinders
Units = cylinders of 4128 * 512 = 2113536 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000f5db

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         961     1982448    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(968, 128, 32) logical=(960, 63, 32)

It also appears that my 1 TB HDD isn't appearing either. Kernel update gone bad?

Thank you in advance for your support.

---

### Post by chaanakya_chiraag on 2010-09-19
Hmmm...so Lucid doesn't recognize the harddrive at all????  Not even in GParted/fdisk?

---

### Post by The_Shady_1 on 2010-09-19
> **chaanakya_chiraag said:**
> Hmmm...so Lucid doesn't recognize the harddrive at all????  Not even in GParted/fdisk?

It did before. All I did was the kernel update last night and it seems like everything went whack. The BIOS recognizes the drive. I see it being initialized when I startup.

---

### Post by Rubi1200 on 2010-09-19
Try running ```
sudo update-grub
``` in Ubuntu and see if that changes anything. 

If not, then post the results of the bootscript linked to at the bottom of my post please.

Thanks.

---

### Post by The_Shady_1 on 2010-09-19
> **Rubi1200 said:**
> Try running ```
sudo update-grub
``` in Ubuntu and see if that changes anything. 

If not, then post the results of the bootscript linked to at the bottom of my post please.

Thanks.

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   976,771,071   976,769,024   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   687,646,259   687,646,197   7 HPFS/NTFS
/dev/sdb2         687,646,718   976,773,119   289,126,402   5 Extended
/dev/sdb5    *    687,646,720   964,947,967   277,301,248  83 Linux
/dev/sdb6         964,950,016   976,773,119    11,823,104  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3046320C4631D378                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        652C0E6F789ABDA2                       ntfs                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        2711f1c8-c832-4adf-bfd9-abfd5c7da029   ext4                                     
/dev/sdb6        7106ece8-feb1-4e99-99e0-368772b7497e   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro)


=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set default="4"
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
search --no-floppy --fs-uuid --set 2711f1c8-c832-4adf-bfd9-abfd5c7da029
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
search --no-floppy --fs-uuid --set 2711f1c8-c832-4adf-bfd9-abfd5c7da029
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=90
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 2711f1c8-c832-4adf-bfd9-abfd5c7da029
	linux	/boot/vmlinuz-2.6.32-24-generic-pae root=UUID=2711f1c8-c832-4adf-bfd9-abfd5c7da029 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 2711f1c8-c832-4adf-bfd9-abfd5c7da029
	echo	'Loading Linux 2.6.32-24-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-24-generic-pae root=UUID=2711f1c8-c832-4adf-bfd9-abfd5c7da029 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 2711f1c8-c832-4adf-bfd9-abfd5c7da029
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 2711f1c8-c832-4adf-bfd9-abfd5c7da029
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=2711f1c8-c832-4adf-bfd9-abfd5c7da029 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=7106ece8-feb1-4e99-99e0-368772b7497e none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 472.4GB: boot/grub/core.img
 460.3GB: boot/grub/grub.cfg
 472.6GB: boot/initrd.img-2.6.32-24-generic-pae
 472.6GB: boot/vmlinuz-2.6.32-24-generic-pae
 472.6GB: initrd.img
 472.6GB: initrd.img.old
 472.6GB: vmlinuz
 472.6GB: vmlinuz.old

---

### Post by Rubi1200 on 2010-09-19
If I understood your original post correctly you can boot into Ubuntu on sdb right?

What about Windows on sda; can you boot into it?

The problem is most likely this:
> => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

Somehow GRUB got installed onto sda even though all the files and the boot flag indicate it should be on sdb (which is how you set things up originally I assume).

---

### Post by The_Shady_1 on 2010-09-19
> **Rubi1200 said:**
> If I understood your original post correctly you can boot into Ubuntu on sdb right?

What about Windows on sda; can you boot into it?

The problem is most likely this:


Somehow GRUB got installed onto sda even though all the files and the boot flag indicate it should be on sdb (which is how you set things up originally I assume).

I am able to boot into Ubuntu. Cant boot into Windows.I think everything went haywire when I bought this 1 TB HDD ~1 month ago. I installed the drive and I think that became sda and messed everything up. I was going back and fourth trying to return it to the state that it was before.Things seem to be mixed up only because I'm now mixed up with boot partitions and such. I had someone help me restore the Win7 boot partition and I know thats located on the TB HDD


With that being said how would I go about restoring things to the way they were with Win 7 and Lucid playing nicely with each other?

---

### Post by Rubi1200 on 2010-09-19
Well, the bootscript shows both sda and sdb to be 500GB drives, so I am not sure what happened to the 1TB drive?

Have you tried reinstalling GRUB as a first step towards a solution?

Here is a guide for that:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

You may have to use Method 3: CHROOT to get the job done and be careful that you mount the right drives/partitions and where you install GRUB.

Hope this helps.

---

### Post by The_Shady_1 on 2010-09-19
I think this is semi fixed. I shutdown/unplugged PC. 1 TB HDD is SATA 3 so I took it off SATA 3 controller put it on SATA 2 controller, went into BIOS and hit load optimized defaults. Computer now boot directly into Win 7, 1 TB HDD shows up.So I don't have GRUB 2 at this point but, I do have Win 7/1 TB HDD fully functional. 

Would this be where I reinstall GRUB 2?

---

