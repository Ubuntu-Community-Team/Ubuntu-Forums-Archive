---
title: "Problem reparing GRUB menus"
date: 2011-01-25
forum: General Help
---

### Post by thewho1050 on 2011-01-25
I installed windows seven after Maverick Meerkat (until that point MM was my only os) which i anticipated would "eat" mu grub menues.  
 
After the installation I booted the live cd, opened a terminal, and attempted to mount the ubuntu partition ( /dev/sda1 ) using the command "sudo mount /dev/sda1.
 
  I got an error that said something like : could not find the file in...  it told me some place i can not remember.   I will post the exact error in a few hours.  What I am looking for is a Step by step on how to repair my grub menues so i can boot from either OS.
 
 Thanks

---

### Post by jimbop99 on 2011-01-25
Try this

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by wilee-nilee on 2011-01-25
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

---

### Post by thewho1050 on 2011-01-25
thanks jimbop.  That is the tutorial i already found.

From a terminal in the live CD, I ran

```
ubuntu@ubuntu:~$ sudo fdisk -l



Disk /dev/sda: 160.0 GB, 160041885696 bytes

255 heads, 63 sectors/track, 19457 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Sector size (logical/physical): 512 bytes / 512 bytes

I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk identifier: 0x000e9acb



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1               1        9562    76800000   83  Linux

/dev/sda2   *        9562       19076    76419072    7  HPFS/NTFS

/dev/sda3           19076       19458     3068929    5  Extended

/dev/sda5           19076       19458     3068928   82  Linux swap / Solaris

```

I then ran

```
ubuntu@ubuntu:~$ sudo mount /dev/sda1

mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab

```

I hope that is more specific

---

### Post by thewho1050 on 2011-01-25
As you requested, the bootscript

```
 Boot Info Script 0.55    dated February 15th, 2010                    



============================= Boot Info Summary: ==============================



 => Windows is installed in the MBR of /dev/sda



sda1: _________________________________________________________________________



    File system:       ext4

    Boot sector type:  -

    Boot sector info:  

    Operating System:  Ubuntu 10.10

    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img



sda2: _________________________________________________________________________



    File system:       ntfs

    Boot sector type:  Windows Vista/7

    Boot sector info:  No errors found in the Boot Parameter Block.

    Operating System:  Windows 7

    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe



sda3: _________________________________________________________________________



    File system:       Extended Partition

    Boot sector type:  -

    Boot sector info:  



sda5: _________________________________________________________________________



    File system:       swap

    Boot sector type:  -

    Boot sector info:  



=========================== Drive/Partition Info: =============================



Drive: sda ___________________ _____________________________________________________



Disk /dev/sda: 160.0 GB, 160041885696 bytes

255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors

Units = sectors of 1 * 512 = 512 bytes

Sector size (logical/physical): 512 bytes / 512 bytes



Partition  Boot         Start           End          Size  Id System



/dev/sda1               2,048   153,602,047   153,600,000  83 Linux

/dev/sda2    *    153,602,048   306,440,191   152,838,144   7 HPFS/NTFS

/dev/sda3         306,442,238   312,580,095     6,137,858   5 Extended

/dev/sda5         306,442,240   312,580,095     6,137,856  82 Linux swap / Solaris





blkid -c /dev/null: ____________________________________________________________



Device           UUID                                   TYPE       LABEL                         



/dev/loop0                                              squashfs                                 

/dev/sda1        d16c1746-6c92-48f1-9d0b-b6a92c827b89   ext4                                     

/dev/sda2        744A964B5A4DCBC6                       ntfs                                     

/dev/sda3: PTTYPE="dos" 

/dev/sda5        daa87a2c-5d9b-4713-bd68-257a01a322e8   swap                                     

/dev/sda: PTTYPE="dos" 



============================ "mount | grep ^/dev  output: ===========================



Device           Mount_Point              Type       Options



aufs             /                        aufs       (rw)

/dev/sr0         /cdrom                   iso9660    (ro,noatime)

/dev/loop0       /rofs                    squashfs   (ro,noatime)





=========================== sda1/boot/grub/grub.cfg: ===========================



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

set root='(hd0,msdos1)'

search --no-floppy --fs-uuid --set d16c1746-6c92-48f1-9d0b-b6a92c827b89

if loadfont /usr/share/grub/unicode.pf2 ; then

  set gfxmode=640x480

  load_video

  insmod gfxterm

fi

terminal_output gfxterm

insmod part_msdos

insmod ext2

set root='(hd0,msdos1)'

search --no-floppy --fs-uuid --set d16c1746-6c92-48f1-9d0b-b6a92c827b89

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

	set root='(hd0,msdos1)'

	search --no-floppy --fs-uuid --set d16c1746-6c92-48f1-9d0b-b6a92c827b89

	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=d16c1746-6c92-48f1-9d0b-b6a92c827b89 ro   quiet splash

	initrd	/boot/initrd.img-2.6.35-24-generic

}

menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {

	recordfail

	insmod part_msdos

	insmod ext2

	set root='(hd0,msdos1)'

	search --no-floppy --fs-uuid --set d16c1746-6c92-48f1-9d0b-b6a92c827b89

	echo	'Loading Linux 2.6.35-24-generic ...'

	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=d16c1746-6c92-48f1-9d0b-b6a92c827b89 ro single 

	echo	'Loading initial ramdisk ...'

	initrd	/boot/initrd.img-2.6.35-24-generic

}

menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {

	recordfail

	insmod part_msdos

	insmod ext2

	set root='(hd0,msdos1)'

	search --no-floppy --fs-uuid --set d16c1746-6c92-48f1-9d0b-b6a92c827b89

	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=d16c1746-6c92-48f1-9d0b-b6a92c827b89 ro   quiet splash

	initrd	/boot/initrd.img-2.6.35-22-generic

}

menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {

	recordfail

	insmod part_msdos

	insmod ext2

	set root='(hd0,msdos1)'

	search --no-floppy --fs-uuid --set d16c1746-6c92-48f1-9d0b-b6a92c827b89

	echo	'Loading Linux 2.6.35-22-generic ...'

	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=d16c1746-6c92-48f1-9d0b-b6a92c827b89 ro single 

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

	set root='(hd0,msdos1)'

	search --no-floppy --fs-uuid --set d16c1746-6c92-48f1-9d0b-b6a92c827b89

	linux16	/boot/memtest86+.bin

}

menuentry "Memory test (memtest86+, serial console 115200)" {

	insmod part_msdos

	insmod ext2

	set root='(hd0,msdos1)'

	search --no-floppy --fs-uuid --set d16c1746-6c92-48f1-9d0b-b6a92c827b89

	linux16	/boot/memtest86+.bin console=ttyS0,115200n8

}

### END /etc/grub.d/20_memtest86+ ###



### BEGIN /etc/grub.d/30_os-prober ###

if [ "x${timeout}" != "x-1" ]; then

  if keystatus; then

    if keystatus --shift; then

      set timeout=-1

    else

      set timeout=0

    fi

  else

    if sleep --interruptible 3 ; then

      set timeout=0

    fi

  fi

fi

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



=============================== sda1/etc/fstab: ===============================



# /etc/fstab: static file system information.

#

# Use 'blkid -o value -s UUID' to print the universally unique identifier

# for a device; this may be used with UUID= as a more robust way to name

# devices that works even if disks are added and removed. See fstab(5).

#

# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc            /proc           proc    nodev,noexec,nosuid 0       0

# / was on /dev/sda1 during installation

UUID=d16c1746-6c92-48f1-9d0b-b6a92c827b89 /               ext4    errors=remount-ro 0       1

# swap was on /dev/sda5 during installation

UUID=daa87a2c-5d9b-4713-bd68-257a01a322e8 none            swap    sw              0       0



=================== sda1: Location of files loaded by Grub: ===================





  51.6GB: boot/grub/core.img

   1.5GB: boot/grub/grub.cfg

   1.3GB: boot/initrd.img-2.6.35-22-generic

   4.4GB: boot/initrd.img-2.6.35-24-generic

  51.6GB: boot/vmlinuz-2.6.35-22-generic

  51.8GB: boot/vmlinuz-2.6.35-24-generic

   4.4GB: initrd.img

   1.3GB: initrd.img.old

  51.8GB: vmlinuz

  51.6GB: vmlinuz.old


```

---

### Post by thewho1050 on 2011-01-25
also, I found somewhere that I could use StartUp-Manager, but nither the terminal nor Synaptic could locate such a program.

any Ideas there anyone?  Thanks

---

### Post by thewho1050 on 2011-01-25
bump

---

### Post by Quackers on 2011-01-25
It seems that grub is not installed on your system.
From a live cd select "try ubuntu" and when the desktop loads, open up a terminal and copy/paste the following commands into the terminal, one at a time, pressing enter after each line please.
```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
In view of your previous attempt, please post again if any error messages are shown during these entries. Thanks.

---

### Post by thewho1050 on 2011-01-26
I ran the two commands without errors.  When i went to Update GRUB as suggested in the [***_tutorial_***]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202"),  I used the command

```
sudo update-grub
```

after mounting the /dev/sda1 partition.   
I recieved the error

```
/user/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?)
```

---

### Post by thewho1050 on 2011-01-26
also Now that I have done that, My windows Partition will not boot either. After the screen that gives me the option to go into BIOS, I am left with a flashing under-strike, which blinks four times in rapid succession, then pauses.

---

### Post by Quackers on 2011-01-26
Sudo update-grub will not run from the live cd desktop.
Does Ubuntu boot now? If so, run sudo update-grub in the terminal and watch to see if the Windows Loader is picked up as grub.cfg is run.

---

### Post by dnairb on 2011-01-26
First, when mounting /dev/sda1 you have to tell the system where to mount it.

This is the method I use to fix a broken grub:

```
sudo mount /dev/sda1 /mnt

sudo grub-install --root-directory=/mnt /dev/sda

sudo umount /dev/sda1
```

then reboot.

This assumes that /dev/sda is your first hdd and that /dev/sda1 is the holds the boot configs.

Run sudo blkid to make sure you are running the commands on the correct hdd/partition

---

### Post by oldfred on 2011-01-26
Because you had the windows boot loader in the MBR you were booting windows directly. Once grub is fixed you should be able to boot both, but the grub.cfg does not have windows yet, so you do not get a grub menu.

You keep trying just part of the grub install commands and then trying to run the update command from the liveCD. 

Only after you have rebooted into Ubuntu run this:
sudo update-grub

Rerun the commands Quacker first gave you and copy & paste so you do not make typos.

If you just get the underscore, try holding the shift key down from BIOS until menu appears. With one system grub does not show menu, but just boots. Then try recovery mode.

---

### Post by thewho1050 on 2011-01-26
> also Now that I have done that, My windows Partition will not boot either. After the screen that gives me the option to go into BIOS, I am left with a flashing under-strike, which blinks four times in rapid succession, then pauses.
_____________



I cant boot ubuntu Anymore

---

### Post by Quackers on 2011-01-26
Then something went wrong, it seems.
Please boot from the live cd and post the output from re-running the boot script, so we can see what's what!
ps. did you ytpe the commands in to the terminal, or did you copy/paste them?

---

### Post by JRV on 2011-01-26
Download the Rescatux disk from this site: [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
Boot this live CD and follow the prompts.

This is the easiest way I know of to fix Grub2.

---

### Post by thewho1050 on 2011-01-26
I typed them.  I am on one computer with an internet connection and another with the problem.  

I ran the sudo blkid  RESULTS:

```
ubuntu@ubuntu:~$ sudo blkid

/dev/loop0: TYPE="squashfs" 

/dev/sda1: UUID="d16c1746-6c92-48f1-9d0b-b6a92c827b89" TYPE="ext4" 

/dev/sda2: UUID="744A964B5A4DCBC6" TYPE="ntfs" 

/dev/sda5: UUID="daa87a2c-5d9b-4713-bd68-257a01a322e8" TYPE="swap" 

/dev/mmcblk0p1: SEC_TYPE="msdos" LABEL="CASIO-DSC" UUID="1715-0BEE" TYPE="vfat"
```

The mount and GRUB install had no errors.  I unmounted then ran sudo blkid.

---

### Post by Cavsfan on 2011-01-26
Don't mean to butt in but this might help. It is from this forum and I have used it,
[[COLOR=blue]_How to restore Grub from a live Ubuntu cd._[/COLOR]]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by Quackers on 2011-01-26
It is possible, then, that you missed a space out - they are critical. It's easily done.

---

### Post by thewho1050 on 2011-01-26
You must be right.  I als didnt unmount the first time.  Anyway i did it all again, and it booted directly into UBUNTU, i then updated grub and can now boot either UBUNTU or windows.  Are there any grub bootloader skins that work with 10.10?

---

### Post by Quackers on 2011-01-26
Excellent :-)
I know you've got 4 legs, but it isn't good to run before you can walk :wink:
I would advise you to enjoy what you've got for the moment :-) It took a while to get this far! 
And, possibly, read more before you jump :-)

---

### Post by thewho1050 on 2011-01-26
Tie me back to earth why don't you....  HAHA thanks I think i will

---

### Post by Quackers on 2011-01-26
munch some tasty grass for a while :-)

---

### Post by Cavsfan on 2011-01-26
> **thewho1050 said:**
> You must be right.  I als didnt unmount the first time.  Anyway i did it all again, and it booted directly into UBUNTU, i then updated grub and can now boot either UBUNTU or windows.  Are there any grub bootloader skins that work with 10.10?

Check out the tutorial in my signature. There are example pics. I added one today as the very last post.

---

