---
title: "All latest grub options will not boot"
date: 2011-01-03
forum: General Help
---

### Post by dazek on 2011-01-03
Hi 

I am a relative noob to ubuntu (6 months) but not to computers!

I am running a dual boot Asus laptop with Vista and Ubuntu

I have numerous versions to boot into in Grub 2 (I understand they are different kernels) - but only one of the older ones ever works - version 32-25

Whenever I select one of the more recent versions (say 35-22), I just get a flashing cursor in the top left of my screen and the computer stays in this state.

Anyway, before I realised these were Kernels, I wanted to clean up all the non working versions from the grub menu - I did this by going to the Synaptic Package Manager and uninstalling the other versions (Linux Kernel Headers and the header files). I had read that Grub 2 would see they were gone and they would not appear in the menu - but they are still there!

Anyway, how do I get the latest kernel versions back (as I guess I should be using the latest one), then get it to work and then clean up the grub menu?? 

I have done a lot of searching around to no avail before posting here!

Many thanks

Darius

---

### Post by Deserttaxguy on 2011-01-03
I'm having the same issue. I am following your thread and hope we get some help. I thinking of just doing a whole new reinstall on my dual boot Win 7 system. I like Ubuntu, but I cant get my desktop to work and my synaptic update manager has a bad list in it. Good luck

---

### Post by 23dornot23d on 2011-01-03
The kernel I just upgraded to is as below

keith@keith-laptop:~$ uname -a
Linux keith-laptop **2.6.35-24-generic** #42-Ubuntu SMP Thu Dec 2 01:41:57 UTC 2010 i686 GNU/Linux


If it was my computer ...... the easiest way and the safest way in my mind is to do this

[I]I have just done this with mine ........ as it was well out of date ....... I needed to add 1496 updates ...... to one of my systems ..... I run quite a few versions of Linux though - but no Windows nowadays. 
( but as far as I know this way to use the update procedure should not affect Windows if it is installed and running properly at the moment )
Grub 2 update is the thing that sometimes caused problems in the past ...... but I think they have sorted most of the old problems with it.

so this is what I did[/I] ( you may also need to do **sudo apt-get install aptitude** ) as its not installed as standard.

[B]sudo aptitude update

sudo aptitude safe-upgrade[/B]

There are other ways - but this is the easiest way to explain ..... and I find is always the safe option for me.

---

### Post by drs305 on 2011-01-03
dazek & Deserttaxguy,

Welcome to the  Ubuntu forums.

dazek, 

Please boot the LiveCD and run the boot info script and post the contents of RESULTS.txt.

[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

Deserttaxguy, watch what we recommend for dazek.

The flashing cursor is probably a video card issue due to recent updates, especially nvidia cards.

You might be able to get your system working by editing the menuentry on boot. Highlight the top selection, press 'e', go to the end of the 'linux' line and replace "quiet splash" with "nomodeset". Then CTRL-x to boot.

If it boots, go to System, Administration, Additional Hardware and add your video driver.

---

### Post by coffeecat on 2011-01-03
> **dazek said:**
> version 32-25

Is a Lucid Lynx (10.04) kernel, whereas:

> **dazek said:**
> 35-22

... is a Maverick Meerkat (10.10) kernel. You need to tell us more about your system. In particular, did you upgrade from Lucid to Maverick?

It sounds as though you haven't uninstalled all the relevant packages using Synaptic. If you had done so, the package manager would have run 'sudo update-grub' for you and regenerated the grub menu without the superfluous menu entries.

Open Synaptic and search for any installed packages with the string '2.6.35-22' in the package name. There are usually 3-4 packages per kernel so you will probably find 1-2 still installed packages. Uninstall them - repeat for other unwanted kernels - and you'll probably find that the grub menu cleans itself up. If not, open a terminal and:

```
sudo update-grub
```However, before you do that:

> **dazek said:**
> Anyway, how do I get the latest kernel versions back (as I guess I should be using the latest one), then get it to work and then clean up the grub menu?? 

Yes, the latest kernel should work and if it doesn't perhaps that needs investigating. If you uninstall all the 2.6.35 kernels (Maverick) you'll be left with a system running a 2.6.32 kernel from Lucid. Perhaps you'd better say more about your system before doing anything.

**EDIT**: @dazek, go with drs305's advice to run the bootscript before doing anything else.

---

### Post by 23dornot23d on 2011-01-03
Follow drs305 ........ as mine is a quick fix ....... 

in the case where it picks the graphics card up and sets it ok ...

in my case I had no graphics at all ..... the safe upgrade grabbed the latest Nvidia driver and kernel and installed both ..... but do

as drs305 says ...... if the graphics is not picking up ..... shown by the flashing cursor then it may be a case of finding the correct graphics driver ...... 

I have been away for a while so am not fully up to date with what has been happening on the graphic driver front .......

But best of luck ....... ):P

---

### Post by dazek on 2011-01-03
Hi Guys

Many thanks for the prompt replies! Do bear in mind that I can get into Ubuntu, albeit with the older Kernel version. 

drs305 - I will do as you suggest. It will be a couple of days as I am away with work for a bit. Yes, I did update from 10.04 to 10.10 (I believe that is Lucid to Maverick!!)

I really would have liked a clean install, but due to the problems I was having with the boot menu, I didn't want to risk messing it up. (Especially as I can't afford to lose this current install of windows due to data therein)

Interestingly, I do have an Nvidia card (Geforce 9300M GS).

Many thanks for the support.

Regards

Darius

---

### Post by 23dornot23d on 2011-01-03
Your graphics card looks as if it is the same as the one I have too 
and the latest Nvidia driver works ok on mine ...... just so you know .......

I run a Acer Aspire 7730 ZG ...... with the Geforce 9300M GS with 512 MB with no problems  ...... 

I did the safe-upgrade about 3 hours ago ....... and all went well .

---

### Post by drs305 on 2011-01-03
@ 23dornot23d,

Since you have the same card, can you tell dazek which driver is listed in the Additional Hardware applet? Is it *nvidia current* or one of the others listed with a specific version?

Thanks for helping.  :-)

---

### Post by 23dornot23d on 2011-01-03
Nvidia Current is working fine ...........

I found out that ...........

  **Aptitude downloads the latest** but left the older one active ..... so I had to go to [B]

additional hardware and pick the latest one to activate it[/B] ........ 

( which is good because if your original works ok - it should then let you get to a working desktop )

 ....... the newest one at this time is ok from doing the **aptitude safe-upgrade** -  

It dropped in the *nvidia current *..... 260.19.06 ......... and its running very well  .... with the Nvidia 9300M GS

[IMG]http://img251.imageshack.us/img251/4879/driver2.png[/IMG]



[B]So this is just to confirm that the latest driver does work ok on the latest kernel at this point in time ............


[/B]As regards setting up Grub 2 and Windows ....... 

I will leave that one with the people that know it best ..... thanks for the nice comment drs305.

> I really would have liked a clean install, but due to the problems I was  having with the boot menu, I didn't want to risk messing it up.  (Especially as I **can't afford to lose this current install of windows  due to data therein**)

Always keep a backup of important data .......... USB drives are so cheap nowadays ....... and it takes less time to restore a backup than
to try to sort out problems if they should occur (either from Windows or Linux). 

Best of luck with getting everything going when you do try to sort things out .....

---

### Post by dazek on 2011-01-09
hi guys - the contents of results.txt below. Also strangely, to get into vista I have to boot into what Grub is calling vista recovery but it is SDA2 which is actually vista. It calls SDA1 vista???
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for (,msdos7)/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  -
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 64. But according to the info from fdisk, 
                       sda6 starts at sector 209262754.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    20,482,874    20,482,812  1c Hidden W95 FAT32 (LBA)
/dev/sda2    *     20,482,875   188,249,669   167,766,795   7 HPFS/NTFS
/dev/sda3         188,249,731   625,141,759   436,892,029   5 Extended
/dev/sda5         188,249,733   209,262,689    21,012,957   7 HPFS/NTFS
/dev/sda6         209,262,754   549,978,024   340,715,271   7 HPFS/NTFS
/dev/sda7         549,978,112   621,965,311    71,987,200  83 Linux
/dev/sda8         621,967,360   625,141,759     3,174,400  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3C98-AC5D                              vfat       RECOVERY                      
/dev/sda2        0A2C2CB32C2C9C27                       ntfs       VistaOS                       
/dev/sda3: PTTYPE="dos" 
/dev/sda5        173CC38544A06919                       ntfs       TEMP                          
/dev/sda6        FA8401C936B06CA2                       ntfs       DATA                          
/dev/sda7        dff78dbf-1bfe-43ea-a534-7b0cfc3f9b31   ext4                                     
/dev/sda8        af8db9b8-e90d-4699-b8d6-a1567a70e268   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda6        /media/sda6              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sr0         /media/Ubuntu 10.10 i386 iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)


=========================== sda7/boot/grub/grub.cfg: ===========================

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
set default="11"
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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set dff78dbf-1bfe-43ea-a534-7b0cfc3f9b31
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set dff78dbf-1bfe-43ea-a534-7b0cfc3f9b31
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set dff78dbf-1bfe-43ea-a534-7b0cfc3f9b31
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=dff78dbf-1bfe-43ea-a534-7b0cfc3f9b31 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set dff78dbf-1bfe-43ea-a534-7b0cfc3f9b31
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=dff78dbf-1bfe-43ea-a534-7b0cfc3f9b31 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set dff78dbf-1bfe-43ea-a534-7b0cfc3f9b31
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=dff78dbf-1bfe-43ea-a534-7b0cfc3f9b31 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set dff78dbf-1bfe-43ea-a534-7b0cfc3f9b31
	echo	'Loading Linux 2.6.35-23-generic ...'
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=dff78dbf-1bfe-43ea-a534-7b0cfc3f9b31 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set dff78dbf-1bfe-43ea-a534-7b0cfc3f9b31
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=dff78dbf-1bfe-43ea-a534-7b0cfc3f9b31 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set dff78dbf-1bfe-43ea-a534-7b0cfc3f9b31
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=dff78dbf-1bfe-43ea-a534-7b0cfc3f9b31 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set dff78dbf-1bfe-43ea-a534-7b0cfc3f9b31
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=dff78dbf-1bfe-43ea-a534-7b0cfc3f9b31 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set dff78dbf-1bfe-43ea-a534-7b0cfc3f9b31
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=dff78dbf-1bfe-43ea-a534-7b0cfc3f9b31 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set dff78dbf-1bfe-43ea-a534-7b0cfc3f9b31
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=dff78dbf-1bfe-43ea-a534-7b0cfc3f9b31 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set dff78dbf-1bfe-43ea-a534-7b0cfc3f9b31
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=dff78dbf-1bfe-43ea-a534-7b0cfc3f9b31 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set dff78dbf-1bfe-43ea-a534-7b0cfc3f9b31
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set dff78dbf-1bfe-43ea-a534-7b0cfc3f9b31
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod fat
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 3c98-ac5d
	chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 0a2c2cb32c2c9c27
	drivemap -s (hd0) ${root}
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

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid      0  0  
# / was on /dev/sda7 during installation
UUID=dff78dbf-1bfe-43ea-a534-7b0cfc3f9b31  /            ext4  errors=remount-ro        0  1  
# swap was on /dev/sda8 during installation
UUID=af8db9b8-e90d-4699-b8d6-a1567a70e268  none         swap  sw                       0  0  
/dev/sda6                                  /media/sda6  ntfs  nls=iso8859-1,umask=000  0  0  

=================== sda7: Location of files loaded by Grub: ===================


 294.6GB: boot/grub/core.img
 294.6GB: boot/grub/grub.cfg
 294.7GB: boot/initrd.img-2.6.32-24-generic
 284.0GB: boot/initrd.img-2.6.32-25-generic
 292.6GB: boot/initrd.img-2.6.35-22-generic
 300.7GB: boot/initrd.img-2.6.35-23-generic
 300.8GB: boot/initrd.img-2.6.35-24-generic
 294.7GB: boot/vmlinuz-2.6.32-24-generic
 294.7GB: boot/vmlinuz-2.6.32-25-generic
 295.3GB: boot/vmlinuz-2.6.35-22-generic
 296.6GB: boot/vmlinuz-2.6.35-23-generic
 296.6GB: boot/vmlinuz-2.6.35-24-generic
 300.8GB: initrd.img
 300.7GB: initrd.img.old
 296.6GB: vmlinuz
 296.6GB: vmlinuz.old

```

---

### Post by dazek on 2011-01-09
thanks for the edit ;)

---

### Post by drs305 on 2011-01-09
The Windows labelling issue is easy to fix. Since you have only the one additional OS (Windows), you can add the real Windows entry into /etc/grub.d/40_custom and then turn off os-prober. This will eliminate the two current Windows entries and replace them with a custom one, whose title you can choose. If you need to access the real Windows entries, you just turn os-prober back on and run 'update'grub'.

To create the custom menu,
Turn off os-prober: 
```
gksu gedit /etc/default/grub /etc/grub.d/40custom
```
Add this line to /etc/default/grub:
> GRUB_DISABLE_OS_PROBER="true"

Next, add the following lines after the existing lines to /etc/grub.d/40_custom (this file should be executable by default):

> menuentry "ENTER TITLE HERE (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 0a2c2cb32c2c9c27
	drivemap -s (hd0) ${root}
	chainloader +1
}

You can remove the *(on /dev/sda2)* portion if you wish as well although it might serve as a reminder for you.

Once you have saved both files, run "sudo update-grub".

As far as the linux entries, I'm not sure which kernel you are currently using successfully. The default entry shows "11", which is not the one you are booting (11 is a memtest entry). 

The blinking cursor is probably a video problem - don't know if you have sorted that out yet or not. I provided one means of resolving that and I think there were other inputs as well.

Once you know which kernels you want to keep (and Lucid or Maverick), you can use Ubuntu Tweak to remove the extra ones:
[HOWTO: Remove Older Kernels via GUI]("http://ubuntuforums.org/showthread.php?t=1587462")
Update grub after removing kernels to remove them from the menu.

---

### Post by dazek on 2011-01-09
the successful kernel is 32-25. I will have a look into the video issue now. Thanks for the help (will also sort the windows issue - I don't mind so much but confusing the rest of the family!!)

Cheers

Daz

---

### Post by drs305 on 2011-01-09
> **dazek said:**
> the successful kernel is 32-25. I will have a look into the video issue now. Thanks for the help (will also sort the windows issue - I don't mind so much but confusing the rest of the family!!)

Cheers

Daz

While you are editing /etc/default/grub:
For the moment at least you may want to change
> DEFAULT=0
to 
> DEFAULT="Ubuntu, with Linux 2.6.32-25-generic"

so that if it autoboots it will boot a working kernel. The main reason I mention it is that the current DEFAULT of "11" isn't going to do you any good. ;-)

---

