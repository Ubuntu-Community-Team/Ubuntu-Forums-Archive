---
title: "[grub2] Windows Vista fails to load"
date: 2010-08-01
forum: General Help
---

### Post by broxen on 2010-08-01
Hi all:

First, let me say sorry for being ignorant of any forum customs or rules.. if this is in the wrong place forgive me.. <-- NEWB

I've been searching all over for a solution to this and haven't been able to find anything. I've tried several tuts/threads with similar issues, but none have fixed my particular problem.

Here's my setup (or how I'd like it to work anyway):
primary hdd: Linux Mint 9
secondary hdd: Windows Vista Ultimate 64bit
external hdd: No OS; Storage/Backup/etc.

I've had Mint 9 installed on the primary drive for some time now and I've always had the external hdd connected... no issues.

Recently I decided to plop a 40gb drive with a fresh install of vista in there. I disconnected the primary drive, connected the 40gb and installed vista... worked fine... reconnected the primary hdd and booted into Grub2... of course Vista didn't show, so once the OS loaded, I ran os-prober and update-grub...

**Now, Vista shows in Grub2 but when clicked upon shows a black screen (1sec) and then reboots the computer...**

Here's my Meierfra script output:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Windows Vista/7
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 9 Isadora
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda2                  63   156,248,189   156,248,127   5 Extended
/dev/sda5                 126   151,364,429   151,364,304  83 Linux
/dev/sda6         151,373,824   156,248,063     4,874,240  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 41.2 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders, total 80418240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048    80,414,719    80,412,672   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   625,137,344   625,137,282   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda2: PTTYPE="dos" 
/dev/sda5        732aa274-a79b-4484-809e-e29ea7513776   ext4                                     
/dev/sda6        baac69bc-fbc0-4f30-bb06-a5653d9ef237   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        AC18A05018A01B7A                       ntfs       Hades                         
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        92708D03708CEEF3                       ntfs       Atlas                         
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sdc1        /media/Atlas             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set 732aa274-a79b-4484-809e-e29ea7513776
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1280x1024
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
search --no-floppy --fs-uuid --set 732aa274-a79b-4484-809e-e29ea7513776
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

### BEGIN /etc/grub.d/06_mint_theme ###
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 732aa274-a79b-4484-809e-e29ea7513776
insmod png
if background_image /boot/grub/linuxmint.png ; then
  set color_normal=white/black
  set color_highlight=white/light-gray
else
  set menu_color_normal=white/black
  set menu_color_highlight=white/light-gray
fi
### END /etc/grub.d/06_mint_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda5)" --class linuxmint --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 732aa274-a79b-4484-809e-e29ea7513776
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=732aa274-a79b-4484-809e-e29ea7513776 ro  vga=795  quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda5) -- recovery mode" --class linuxmint --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 732aa274-a79b-4484-809e-e29ea7513776
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=732aa274-a79b-4484-809e-e29ea7513776 ro single  vga=795
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 732aa274-a79b-4484-809e-e29ea7513776
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 732aa274-a79b-4484-809e-e29ea7513776
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sdb1)" {
	insmod ntfs
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set ac18a05018a01b7a
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=732aa274-a79b-4484-809e-e29ea7513776 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=baac69bc-fbc0-4f30-bb06-a5653d9ef237 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  30.2GB: boot/grub/core.img
   4.4GB: boot/grub/grub.cfg
  30.3GB: boot/initrd.img-2.6.32-21-generic
  30.2GB: boot/vmlinuz-2.6.32-21-generic
  30.3GB: initrd.img
  30.2GB: vmlinuz
```

As I mentioned, I've tried several threads on this forum and other random linux blogs, etc.. I'll try anything again, but to summarize what I've attempted:
[LIST]
[*]fixmbr and fixboot from Vista's repair console
[*]os-prober and update-grub... again and again...
[*]Manually entering an entry for Windows into grub.d\40_Custom
[*]Disconnecting the Linux drive and booting straight into Windows (works!)
[/LIST]

I'd really rather shine Vista all together.. but I need windoze for a few specialty apps that fail under Wine.

Any help is much appreciated!
Broxen

---

### Post by prodigy_ on 2010-08-01
The problem isn't in Grub.

You said you disconnected your primary HDD when you were installing Vista. Most probably now Vista bootloader (BCD) points to an incorrect disk as the result. So you'll need a tool like [EasyBCD](http://neosmart.net/dl.php?id=1) to correct this.

---

### Post by oldfred on 2010-08-02
Grub usually adds a line to make windows think it is still first..
drivemap -s (hd1) ${root}

I would copy your windows boot stanza into 40_custom and add the drivemap command.

Copy the windows entry from this:
gedit /boot/grub/grub.cfg
Copy them to and edit :
gksudo gedit /etc/grub.d/40_custom
then:
sudo update-grub

or paste this into 40_custom and update grub.

menuentry "Windows Vista (loader) (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set ac18a05018a01b7a
    drivemap -s (hd1) ${root}
    chainloader +1

If this works we can turn off the osprober so you do not have two entries.
In /etc/default/grub I added this:
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

---

### Post by broxen on 2010-08-02
Hi All:

Thank you prodigy_ and oldfred for your help.


**prodigy_:**
> you'll need a tool like EasyBCD to correct this.
[INDENT]I downloaded EasyBCD and have set it up so that Linux Mint (via Grub2) is chainloaded through Vista Bootloader. I also tried to repair the MBR and Bootloader by using the apps internal utilities.

Now if I set my vista hdd as the master in the bios, I can use Vista Bootloader to load both operating systems. This works fine and EasyBCD is a great tool, however I'd much rather use grub2, if possible.

Or did I misunderstand? Was I supposed to use a tool in EasyBCD to fix the problem? How do I do that?[/INDENT]



**oldfred:**
> drivemap -s (hd1) ${root}
[INDENT]I copied the text from grub.cfg to 40_custom, added the drivemap line, updated grub and then changed the permissions on 30_os-prober, as instructed.

Unfortunately I receive the same result: Selecting Windows Vista from Grub2 results in a black screen (1sec) and then reboot of the system...[/INDENT]



**Summary:**
I've undone the EasyBCD for now, as for me, its easier to just use my bios to boot into my vista hdd directly than to sit through two bootloaders (BCD -> Grub2 -> Mint9)

I'd like to use grub2 if possible.. Any other ideas? Could it be b/c I've installed Vista x64 alongside Mint 9 x32 and grub has some sort of hang-up over that? (seems like a longshot, but maybe they don't want to play nice?)

Any ideas are welcome. I appreciate everyone's help!

Broxen

---

### Post by oldfred on 2010-08-02
Most cases have windows on sda and Ubuntu on sdb. I have had issues with grub and drive numbers. My drives in Ubuntu sda, sdb & sdc never change, but if I boot sdc drive that becomes hd0, if I boot sdb that becomes hd0. If I have my bootable USB flash drive plugged in BIOS makes it first and grub calles it hd0.

I might at the grub menu use e  for edit and experiment with hd0 in the drivemap command. I have found the search command overrides a incorrect hdX assignment so boot order on matters sometimes in grub. 

So windows boots ok from BIOS? 

Another option to add to 40_custom if you want to try, this chainloads to the MBR of hd1 with no checking so if it does not work I think it just crashes:

menuentry "Windows Vista (loader) (MBR of sdb)" {
    set root='(hd1)'
    chainloader +1

It was this type of boot where I discovered my grub hd numbering was wrong but I could edit the menu entry (change 0 to 1 for example)  and then it worked when the drive numbers were not correct. If you had a USB drive that become drive 0 then it may be that your sdb is drive 2.

---

### Post by broxen on 2010-08-08
Hi All:

Thanks again for all your help. I've tried some things and still have had no luck. I'd really rather use Grub2, but I may have to use EasyBCD?

And thank you oldfred for your help. Here's what happened when I tried your suggestions:
> **oldfred said:**
> 
I might at the grub menu use e  for edit and experiment with hd0 in the drivemap command. I have found the search command overrides a incorrect hdX assignment so boot order on matters sometimes in grub.
Tried various hd#s and received the same result (weird...) black screen and restart.

> **oldfred said:**
> 
So windows boots ok from BIOS?
Yes, if I change the boot order in the BIOS, Windows will load perfectly fine. Grub2 doesn't need to be on the windows partition right? B/c it simply chainloads BCD.

> **oldfred said:**
> 
Another option to add to 40_custom if you want to try, this chainloads to the MBR of hd1 with no checking so if it does not work I think it just crashes:

menuentry "Windows Vista (loader) (MBR of sdb)" {
    set root='(hd1)'
    chainloader +1


No difference =/ Black screen, reboot.

I also snooped around more on the internet and tried this:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:GTP_MS_DOS](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:GTP_MS_DOS)

As it looks very similiar to my setup/problem... however, it did not have any discernible effect.

I'm open to any other ideas... should I try reinstalling Vista? Reinstalling grub?

Broxen

---

### Post by oldfred on 2010-08-08
I am one to try a variety of alternatives, since I really do not know the correct answer.

menuentry "Windows Vista (loader) (MBR of sdb)" {
    set root='(hd1)'
                             drivemap -s (hd1) (hd0)
    chainloader +1

menuentry "Windows Vista (loader) (sdb1)" {
    set root='(hd1,1)'
drivemap -s (hd1) (hd0)
    chainloader +1

I would add these two entries and then try changing every hd1 to hd0 and with or without the drivemap command.

I do know that if I boot sdc then sdc is hd0 in grub and if I chainload to sda I have to use hd1. But if I boot sda my chainboot to hd1 is to sdb, so numbers vary depending on which drive you actually use to boot.

Windows often likes to be first. You could change SATA ports on motherboard so the windows drive is first. You may have to use bcdedit then to get windows to see that it is hd0 not hd1.

---

