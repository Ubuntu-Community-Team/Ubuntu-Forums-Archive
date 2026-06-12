---
title: "Windows 7 installed first Ubuntu 10.10 2 drives dual boot help"
date: 2010-10-12
forum: General Help
---

### Post by ejones on 2010-10-12
Installed Ubuntu 10.10 on 2nd drive on a windows 7 pro machine.

The only way I can get to Ubuntu is with the F8 key on boot up.

The Ubuntu drive is an IDE 120 gig with partitions 4 gig for swap, 23 gig for root and balance to /home.

I tried to use EasyBCD 2.0 pointing to the / directory on the Ubuntu drive. all I get are error messages and a destroyed MBR. I have restored it several times tonight!

not sure what to do next 

thanks

---

### Post by Quackers on 2010-10-12
Welcome to UbuntuForums :-)
Can you go to the link below and download the file to your desktop then in a terminal type the command given on that site. It will produce a Results.txt file on your desktop. Please copy/paste the contents of that file in your next post inside CODE tags (press New Reply then click on the # symbol in the top bar, then paste your file in between the code tags) as this preserves its format.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by ejones on 2010-10-13
Thanks here is the file
edddie

 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048     7,813,119     7,811,072  82 Linux swap / Solaris
/dev/sda2           7,815,166   234,440,703   226,625,538   5 Extended
/dev/sda5           7,815,168    56,641,535    48,826,368  83 Linux
/dev/sda6          56,643,584   234,440,703   177,797,120  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048       206,847       204,800   7 HPFS/NTFS
/dev/sdb2    *        206,848   488,394,751   488,187,904   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
81 heads, 63 sectors/track, 122504 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   625,142,447   625,142,385   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        23010c6a-cd4f-425d-ae57-b3f6d35e6ee4   swap                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        f3062054-98e2-4b43-9d77-4b6158a2407d   ext4                                     
/dev/sda6        2efb0474-5905-4d86-b99d-d80fc21a5c54   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        6836A67E36A64CBE                       ntfs       System Reserved               
/dev/sdb2        D6A4AA60A4AA42BB                       ntfs       Windows Boot Drive            
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        4CCE16F8CE16D9D2                       ntfs       Documents                     
/dev/sdc: PTTYPE="dos" 
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda6        /home                    ext4       (rw,commit=0)
/dev/sdb2        /media/Windows Boot Drive fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1        /media/System Reserved   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set f3062054-98e2-4b43-9d77-4b6158a2407d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set f3062054-98e2-4b43-9d77-4b6158a2407d
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set f3062054-98e2-4b43-9d77-4b6158a2407d
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=f3062054-98e2-4b43-9d77-4b6158a2407d ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set f3062054-98e2-4b43-9d77-4b6158a2407d
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=f3062054-98e2-4b43-9d77-4b6158a2407d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set f3062054-98e2-4b43-9d77-4b6158a2407d
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set f3062054-98e2-4b43-9d77-4b6158a2407d
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 6836a67e36a64cbe
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda5       /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=2efb0474-5905-4d86-b99d-d80fc21a5c54 /home           ext4    defaults        0       2
/dev/sda1       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  19.1GB: boot/grub/core.img
  23.8GB: boot/grub/grub.cfg
   4.7GB: boot/initrd.img-2.6.35-22-generic
  19.1GB: boot/vmlinuz-2.6.35-22-generic
   4.7GB: initrd.img
  19.1GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  00 73 00 69 00 76 00 65  00 46 00 61 00 63 00 65  |.s.i.v.e.F.a.c.e|
00000010  00 74 00 50 00 72 00 6f  00 68 00 69 00 62 00 69  |.t.P.r.o.h.i.b.i|
00000020  00 74 00 65 00 64 00 00  31 53 00 63 00 68 00 5f  |.t.e.d..1S.c.h._|
00000030  00 44 00 75 00 70 00 4d  00 61 00 78 00 49 00 6e  |.D.u.p.M.a.x.I.n|
00000040  00 63 00 6c 00 75 00 73  00 69 00 76 00 65 00 46  |.c.l.u.s.i.v.e.F|
00000050  00 61 00 63 00 65 00 74  00 00 39 53 00 63 00 68  |.a.c.e.t..9S.c.h|
00000060  00 5f 00 4d 00 61 00 78  00 49 00 6e 00 63 00 6c  |._.M.a.x.I.n.c.l|
00000070  00 75 00 73 00 69 00 76  00 65 00 46 00 61 00 63  |.u.s.i.v.e.F.a.c|
00000080  00 65 00 74 00 49 00 6e  00 76 00 61 00 6c 00 69  |.e.t.I.n.v.a.l.i|
00000090  00 64 00 00 3f 53 00 63  00 68 00 5f 00 4d 00 61  |.d..?S.c.h._.M.a|
000000a0  00 78 00 45 00 78 00 63  00 6c 00 75 00 73 00 69  |.x.E.x.c.l.u.s.i|
000000b0  00 76 00 65 00 46 00 61  00 63 00 65 00 74 00 50  |.v.e.F.a.c.e.t.P|
000000c0  00 72 00 6f 00 68 00 69  00 62 00 69 00 74 00 65  |.r.o.h.i.b.i.t.e|
000000d0  00 64 00 00 31 53 00 63  00 68 00 5f 00 44 00 75  |.d..1S.c.h._.D.u|
000000e0  00 70 00 4d 00 61 00 78  00 45 00 78 00 63 00 6c  |.p.M.a.x.E.x.c.l|
000000f0  00 75 00 73 00 69 00 76  00 65 00 46 00 61 00 63  |.u.s.i.v.e.F.a.c|
00000100  00 65 00 74 00 00 39 53  00 63 00 68 00 5f 00 4d  |.e.t..9S.c.h._.M|
00000110  00 61 00 78 00 45 00 78  00 63 00 6c 00 75 00 73  |.a.x.E.x.c.l.u.s|
00000120  00 69 00 76 00 65 00 46  00 61 00 63 00 65 00 74  |.i.v.e.F.a.c.e.t|
00000130  00 49 00 6e 00 76 00 61  00 6c 00 69 00 64 00 00  |.I.n.v.a.l.i.d..|
00000140  3f 53 00 63 00 68 00 5f  00 4d 00 69 00 6e 00 49  |?S.c.h._.M.i.n.I|
00000150  00 6e 00 63 00 6c 00 75  00 73 00 69 00 76 00 65  |.n.c.l.u.s.i.v.e|
00000160  00 46 00 61 00 63 00 65  00 74 00 50 00 72 00 6f  |.F.a.c.e.t.P.r.o|
00000170  00 68 00 69 00 62 00 69  00 74 00 65 00 64 00 00  |.h.i.b.i.t.e.d..|
00000180  31 53 00 63 00 68 00 5f  00 44 00 75 00 70 00 4d  |1S.c.h._.D.u.p.M|
00000190  00 69 00 6e 00 49 00 6e  00 63 00 6c 00 75 00 73  |.i.n.I.n.c.l.u.s|
000001a0  00 69 00 76 00 65 00 46  00 61 00 63 00 65 00 74  |.i.v.e.F.a.c.e.t|
000001b0  00 00 39 53 00 63 00 68  00 5f 00 4d 00 69 00 78  |..9S.c.h._.M.i.x|
000001c0  53 e6 83 fe ff ff 02 00  00 00 00 08 e9 02 00 fe  |S...............|
000001d0  ff ff 05 fe ff ff 02 08  e9 02 00 00 99 0a 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg

---

### Post by lindsay7 on 2010-10-13
I think you need to reinstall the windows mbr.  Here is a link on how to do it.

[http://www.tomstricks.com/how-to-repair-and-restore-windows-vista-master-boot-record-mbr/](http://www.tomstricks.com/how-to-repair-and-restore-windows-vista-master-boot-record-mbr/)

Download a windows 7 installation repair disk for the internet if you do not have the original install disk for your windows 7 instllation.

After you do this you will need to reinstall grub to your system. I will try to find my file on how to do this and give you the info.

Here is what you need,

[http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html](http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html)


Here is the web site to get the repair install disk,

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

---

### Post by ejones on 2010-10-13
As directed I repaired the windows 7 MBR and rebuilt the BCD -  Windows 7 boots up correctly.

When I attempted the grub2 rebuild and attempted rebooting again windows 7 boots but then when I use the F8 key to boot the linux drive I got what looked like a command screen with "grub rescue>."  I could not reboot the linux disk.

I have now re-installed ubuntu for the forth time in this set of attempts to use linux/ubuntu.  This is probably the fifth time over the years I have tried to move to linux.  Its very disheartening to say the least

BTW:  I have Ubuntu re-installed again.  The only way I can access it is with the F8 key.

do I need to redo the boot info script>

---

### Post by Quackers on 2010-10-13
ejones, just out of interest, what is your hardware setup? Are all drives internal or are usb drives part of it? Thanks

---

### Post by ejones on 2010-10-13
On this computer all hard drives are internal.  1 is IDE 120 gig  with the Linux installation.  There is a SATA 250 gig with windows 7 pro installed and no important programs at this time.  In addition there is another SATA 320 Gig I hope to use as a storage device for both systems.  

I have a usb hard drive 500gig for backup purposes.  It has not been attached to the computer since the re-build.

The machine also has a card-reader multi-types, a DVD read/writer and 3.5 floppy disk drive.  It has 4 gig RAM and a dual dvi monitor card Nvidia


Thanks
eddie

---

### Post by Quackers on 2010-10-13
Thanks for that ejones.

---

### Post by Mark Phelps on 2010-10-13
Are you doing the following repeatedly:
1) Repairing Win7 boot, checking that it boots OK
2) Reinstalling GRUB -- with the Win7 drive still connected
3) Attempting to reboot Ubuntu -- but this fails?

IF so, recommend the following:
1) If necessary, repair Win7 boot again, confirm that it boots OK
2) Disconnect ALL but the drive with which you wish to boot Ubuntu
3) Boot from the Ubuntu CD, repair GRUB on that SINGLE drive
4) Reconnect the other drives, but continue to boot from the Ubuntu drive
5) Boot into Ubuntu, open a terminal, run "sudo update-grub".  This SHOULD find Win7 and add an entry for it.

When you reboot, you should get entries for Ubuntu and Win7, and they should work now.

---

### Post by oldfred on 2010-10-13
When you go into the BCD does windows think it is drive 0 or drive 1?

Grub used to add a drivemap command to make windows think it was drive 0 when it was seen by grub as drive 1. 

I have even had issues with chainloading grub2 as the boot drive is always drive 0, but some settings with chainloading follow sda, sdb, sdc etc order where sda is drive 0.

In fact my XP on sda1 has the drivemap.

menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 04b05b70b05b6768
    drivemap -s (hd0) ${root}
    chainloader +1
}

---

### Post by ejones on 2010-10-13
Well, Well I managed to kill everything.

I am re-formating drives now.  

Un-decided as to continue with linux

Thanks for all your help!  A big improvement since my last effort. :)

eddie

---

### Post by Quackers on 2010-10-13
ejones, did you get the private message?

---

### Post by ejones on 2010-10-13
Hi Quackers,

I got the private message, I went to bios and changed the boot drive to the disk ubunta was installed on.  It worked! 

I got the Grub at bootup but had a nagging entry.  Tried to use easybcd to fix the problem and lost the ability to boot either windows or Ubuntu. The win7 disk said it could not repair the problem?  

Still re-formatting drives now.  I will re-install the win7 pro but ----

Thanks again

eddie

---

### Post by Quackers on 2010-10-13
Multiple drives seem to bring multiple problems to grub, it seems. I hope things go better next time :-)

---

### Post by oldfred on 2010-10-13
I have seen few issue when windows is on the first drive and many issues when windows is on an additional drive, but it works for some. Not sure what settings are different between them.

I have XP on sda and Ubuntu on sdb and sdc and have not had any issues, other than drive numbers changing with chainboots.

---

### Post by Quackers on 2010-10-14
oldfred, I think my problems were exacerbated by Sony's insistence on locking the bios. Having 2 hard drives in the laptop with the bios only looking at the first drive for booting (even though that's my Windows Vista drive) means I have to install grub to the first drive's mbr as well as the mbr on the second drive (where Ubuntu is). Otherwise it just boots Vista directly.

---

### Post by oldfred on 2010-10-14
That may prevent the drive number issue as then the first drive will still be sda as that is the MBR your are booting.

That is more like the old IDE drives with primary and secondary channels and master & slave drives. You could only boot the primary master.

---

### Post by ejones on 2010-10-14
One more time

I found an answer and it works.

There are 3 parts in a dual drive setup.

First the BIOS - Thanks Quacker for showing me the way
Next the windows drive (drive 0)
Finally the linux drive (drive 1)
I also have a 3rd drive - Data. (drive 2)

What worked.

1. Set BIOS to Boot the Windows drive (drive 0)
2. Install Windows (get it like you want it)
3. Install Linux on linux drive (drive 1)
4. Set BIOS to Boot the linux drive (drive 1)

Now Grub2 comes up with all the choices and boots correctly.

For me this one can be marked [Solved]

Thanks to everybody for your help
eddie

---

### Post by Quackers on 2010-10-14
Excellent! Perseverence wins the day :-) Nice one.
(If you click on Thread Tools near the top right of the page you can select Solved)

---

