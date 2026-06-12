---
title: "Cannot access Ubuntu after Fedora Install.[Help pls]"
date: 2011-06-13
forum: General Help
---

### Post by kmdent on 2011-06-13
I installed Fedora 15 today, and after the install, the boot loader would not allow me to access my Ubuntu partition. I have been doing on some reading on this, and have figured out that the issue is that my grub.conf doesn't have a title for Ubuntu. My problem is that I don't know how to add the title successfully. There is also a windows partition on here. At this point, i just want ubuntu back. I could scrap both windows and fedora if I had to.

The following is my grub.conf file:

#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,7)
#          kernel /vmlinuz-version ro root=/dev/mapper/vg_intel-lv_root
#          initrd /initrd-[generic-]version.img
#boot=/dev/sda
default=0
timeout=5
splashimage=(hd0,7)/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.38.6-26.rc1.fc15.i686)
        root (hd0,7)
        kernel /vmlinuz-2.6.38.6-26.rc1.fc15.i686 ro root=/dev/mapper/vg_intel-lv_root rd_LUKS_UUID=luks-ea29e6e7-bc91-4630-a743-3a69ae69856d rd_LVM_LV=vg_intel/lv_root rd_LVM_LV=vg_intel/lv_swap rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=us rhgb quiet
        initrd /initramfs-2.6.38.6-26.rc1.fc15.i686.img
title Other
        rootnoverify (hd0,0)
        chainloader +1


#################################################################

THIS IS A LS OF THE /BOOT DIRECTORY
#################################################################
config-2.6.38.6-26.rc1.fc15.i686
efi
elf-memtest86+-4.10
grub
initramfs-2.6.38.6-26.rc1.fc15.i686.img
lost+found 
memtest86+-4.10
System.map-2.6.38.6-26.rc1.fc15.i686
vmlinuz-2.6.38.6-26.rc1.fc15.i686




#################################################################

THIS IS "fdisk -l"
#################################################################
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3e2fb21f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      731135      364544    7  HPFS/NTFS/exFAT
/dev/sda2          731136   197075125    98171995    7  HPFS/NTFS/exFAT
/dev/sda3       197076990   625141759   214032385    5  Extended
/dev/sda5       620969984   625141759     2085888   82  Linux swap / Solaris
/dev/sda6       197076992   210812927     6867968   82  Linux swap / Solaris
/dev/sda7       210814976   487938047   138561536   83  Linux
/dev/sda8       487940096   488964095      512000   83  Linux
/dev/sda9       488966144   620959743    65996800   83  Linux

Partition table entries are not in disk order

Disk /dev/mapper/luks-ea29e6e7-bc91-4630-a743-3a69ae69856d: 67.6 GB, 67578626048 bytes
255 heads, 63 sectors/track, 8215 cylinders, total 131989504 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/luks-ea29e6e7-bc91-4630-a743-3a69ae69856d doesn't contain a valid partition table

Disk /dev/mapper/vg_intel-lv_swap: 4227 MB, 4227858432 bytes
255 heads, 63 sectors/track, 514 cylinders, total 8257536 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/vg_intel-lv_swap doesn't contain a valid partition table

Disk /dev/mapper/vg_intel-lv_root: 53.7 GB, 53687091200 bytes
255 heads, 63 sectors/track, 6527 cylinders, total 104857600 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/vg_intel-lv_root doesn't contain a valid partition table

Disk /dev/mapper/vg_intel-lv_home: 9630 MB, 9630121984 bytes
255 heads, 63 sectors/track, 1170 cylinders, total 18808832 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


################################################################


I would really appreciate any advice you could give me.

Thanks,
Kyle

---

### Post by wildmanne39 on 2011-06-13
Boot Script

Hi, post the information from this script so we can see where everything is located:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans

Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by nilarimogard on 2011-06-14
This happens to me all the time after trying out some new Linux distro. Basically this is what you must do (booting from an Ubuntu Live CD):

[IMG]http://www.netupd8.com/w8img/jh7onq.jpg[/IMG]

And then update Grub ("sudo update-grub").

You can find the complete instructions here: [fix / restore Grub2]("http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html")

---

### Post by kmdent on 2011-06-14
> **nilarimogard said:**
> This happens to me all the time after trying out some new Linux distro. Basically this is what you must do (booting from an Ubuntu Live CD):

[IMG]http://www.netupd8.com/w8img/jh7onq.jpg[/IMG]

And then update Grub ("sudo update-grub").

You can find the complete instructions here: [fix / restore Grub2]("http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html")

This worked perfectly. That screenshot explained it all! Thanks for the help guys!

Kyle

---

### Post by nilarimogard on 2011-06-14
You're welcome :)

---

