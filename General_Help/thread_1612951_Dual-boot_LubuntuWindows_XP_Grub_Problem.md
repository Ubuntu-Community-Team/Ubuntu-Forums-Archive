---
title: "Dual-boot Lubuntu/Windows XP Grub Problem"
date: 2010-11-03
forum: General Help
---

### Post by Darth Penguin on 2010-11-03
After the last Lubuntu update Windows XP disappeared from the grub and it doesn't appear on the OS list. Is there any way I can fix or restore the grub to display XP again? Thanks.

I ran TestDisk and the XP partition is there undamaged, it also appears in the file system and I can access the files in Lubuntu; it's just not appearing in the grub anymore.

---

### Post by papibe on 2010-11-03
You could try to update grub, reboot and maybe you'll be lucky:
```
$ sudo update-grub
```

If not, you may want to follow what I did in a similar situation with Vista. Check my post [here]("http://ubuntuforums.org/showpost.php?p=9498158&postcount=1155").

Good Luck!

---

### Post by Darth Penguin on 2010-11-03
Thank you! I'll try that. :)

---

### Post by Quackers on 2010-11-03
If things don't improve after sudo update-grub, would you please have a look in /etc/grub.d and see if 30_os-prober file is present? It seems lubuntu has shipped without it on occasions.

---

### Post by Darth Penguin on 2010-11-04
The file is there. Thank you for your assistance Quackers.

---

### Post by Quackers on 2010-11-04
You're welcome. Is your problem now resolved?

---

### Post by h4xor66 on 2010-11-10
i saw that a ton of people are having problems with grub in lubuntu so i installed it on one of my boxes tonight ... and oh yeah there are problems ... to begin with the install sucks , you have the option to over write all data on the hard drive or manually configure the linux partitions ( how many new adopters know how to do that ?)  if you get past that and it installs , your xp partition will not show up in grub several attempts to re install grub and install os-prober have not helped  i've tried to manually edit grub when i type sudo grub it says command unknown ... thats as far as i've gotten 

anybody else have any ideas ??

---

### Post by wilee-nilee on 2010-11-10
Lubuntu is grub2 right. We are talking about the 10.04 is this correct?

---

### Post by h4xor66 on 2010-11-10
> **wilee-nilee said:**
> Lubuntu is grub2 right. We are talking about the 10.04 is this correct?

in my case it's 10.10 ... i just tried to install grub from the live cd and fix grub like you would with ubuntu 

sudo grub
root (hd0,0)
setup (hd0)  at this command it says can not setup partition, partition can not be mounted 

i've even edited menu.lst and added the lines that would be there in a normal ubuntu install ( IE, title windows xp blah blah blah ) saved it and rebooted ... still doesn't appear in the startup menu 

im actually stumped ... i've edited grub many times in dual boot ubuntu systems ... it just isn't working with lubuntu

---

### Post by wilee-nilee on 2010-11-10
> **h4xor66 said:**
> in my case it's 10.10 ... i just tried to install grub from the live cd and fix grub like you would with ubuntu 

sudo grub
root (hd0,0)
setup (hd0)  at this command it says can not setup partition, partition can not be mounted 

i've even edited menu.lst and added the lines that would be there in a normal ubuntu install ( IE, title windows xp blah blah blah ) saved it and rebooted ... still doesn't appear in the startup menu 

im actually stumped ... i've edited grub many times in dual boot ubuntu systems ... it just isn't working with lubuntu

Post the bootscript in my signature in code tags, and we will have look. You can just paste the text to the reply and highlight it then click on the # in the reply panel to wrap the text in code tags.

I downloaded 10.04 to load on a virtual so I will load it as we work if your still on.

---

### Post by wilee-nilee on 2010-11-10
10.04 installed in Vbox with no problems. If you want to reload grub follow this guide. you just need 3 commands the first to identify the partitions then the next two read carefully.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

@h4xor66 are you familiar with grub2 I think your trying to edit in the manner of grub-legacy it doesn't work.

---

### Post by h4xor66 on 2010-11-10
> **wilee-nilee said:**
> 10.04 installed in Vbox with no problems. If you want to reload grub follow this guide. you just need 3 commands the first to identify the partitions then the next two read carefully.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

@h4xor66 are you familiar with grub2 I think your trying to edit in the manner of grub-legacy it doesn't work.

not sure how to get you my boot script or where it's located 

i tried ... for the 4th time to reinstall grub here is what happens 


```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb74510e2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1003     8056566    7  HPFS/NTFS
/dev/sda2            1004        2434    11493377    5  Extended
/dev/sda5            1004        2100     8804352   83  Linux
/dev/sda6            2100        2434     2688000   82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sda
Installation finished. No error reported.
ubuntu@ubuntu:~$ 

---------------------------------------------------------------
after installing grub 
sudo update-grub --------
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.35-22-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done
```



you can see that XP is on sda1 and linux is on sda5 , i installed grub to sda5 rebooted updated grub and my windows partition is not found 


so grub is there it just doesn't see xp  .... i need to know how to manually add an option to the grub menu.lst  ... im going to go look at the menu.lst now to see what it looks like



thanks for your help by the way ...

---

### Post by wilee-nilee on 2010-11-10
Updating /boot/grub/**menu.lst** ... done

This is grub legacy, not grub2

The script is a link in my signature go to the site and download the script put it on the desktop and run this command.
```
sudo bash ~/Desktop/boot_info_script*.sh 
```

A new file will appear open it copy the text come back to the thread and paste the text and highlight it and click on the # .

---

### Post by h4xor66 on 2010-11-10
> **wilee-nilee said:**
> Updating /boot/grub/**menu.lst** ... done

This is grub legacy, not grub2

The script is a link in my signature go to the site and download the script put it on the desktop and run this command.
```
sudo bash ~/Desktop/boot_info_script*.sh 
```

A new file will appear open it copy the text come back to the thread and paste the text and highlight it and click on the # .

 ```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders, total 39102336 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    16,113,194    16,113,132   7 HPFS/NTFS
/dev/sda2          16,113,662    39,100,415    22,986,754   5 Extended
/dev/sda5          16,113,664    33,722,367    17,608,704  83 Linux
/dev/sda6          33,724,416    39,100,415     5,376,000  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        AA841D9D841D6D57                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        9a0180e1-7094-4fe5-928c-d568cac11324   ext4                                     
/dev/sda6        164f6dec-f329-4323-9c61-a9b32c9596bb   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptOut

=========================== sda5/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=9a0180e1-7094-4fe5-928c-d568cac11324 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9a0180e1-7094-4fe5-928c-d568cac11324

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 10.10, kernel 2.6.35-22-generic
uuid		9a0180e1-7094-4fe5-928c-d568cac11324
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=9a0180e1-7094-4fe5-928c-d568cac11324 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-22-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid		9a0180e1-7094-4fe5-928c-d568cac11324
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=9a0180e1-7094-4fe5-928c-d568cac11324 ro  single
initrd		/boot/initrd.img-2.6.35-22-generic

title		Chainload into GRUB 2
root		9a0180e1-7094-4fe5-928c-d568cac11324
kernel		/boot/grub/core.img

title		Ubuntu 10.10, memtest86+
uuid		9a0180e1-7094-4fe5-928c-d568cac11324
kernel		/boot/memtest86+.bin

title		Windows XP Professional  ## I added these lines per example at top of menu.lst
root		(hd0,0)
makeactive
chainloader	+1

### END DEBIAN AUTOMAGIC KERNELS LIST

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
search --no-floppy --fs-uuid --set 9a0180e1-7094-4fe5-928c-d568cac11324
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 9a0180e1-7094-4fe5-928c-d568cac11324
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
	search --no-floppy --fs-uuid --set 9a0180e1-7094-4fe5-928c-d568cac11324
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=9a0180e1-7094-4fe5-928c-d568cac11324 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 9a0180e1-7094-4fe5-928c-d568cac11324
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=9a0180e1-7094-4fe5-928c-d568cac11324 ro single 
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
	search --no-floppy --fs-uuid --set 9a0180e1-7094-4fe5-928c-d568cac11324
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 9a0180e1-7094-4fe5-928c-d568cac11324
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
# / was on /dev/sda5 during installation
UUID=9a0180e1-7094-4fe5-928c-d568cac11324 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=164f6dec-f329-4323-9c61-a9b32c9596bb none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  10.5GB: boot/grub/core.img
  10.5GB: boot/grub/grub.cfg
  10.5GB: boot/grub/menu.lst
   9.2GB: boot/initrd.img-2.6.35-22-generic
  10.6GB: boot/vmlinuz-2.6.35-22-generic
   9.2GB: initrd.img
  10.6GB: vmlinuz

```

---

### Post by wilee-nilee on 2010-11-10
```
sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot**/grub/menu.lst **/boot**/grub/grub.cfg** /etc/fstab 
                       /boot/grub/core.img
```

So what we have here is at the least grub-legacy and grub2 together in this part, I high lighted the grub-legacy and the grub2=grub.cfg. 

Here is a link to purge both and restore to just grub2, which once you get used to it personally, I feel is much easier to use. Follow the Chroot portion.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Good job on getting the script up it is confusing at first I know it was for me.;)

---

### Post by h4xor66 on 2010-11-10
> **wilee-nilee said:**
> 
So what we have here is at the least grub-legacy and grub2 together in this part, I high lighted the grub-legacy and the grub2=grub.cfg. 

Here is a link to purge both and restore to just grub2, which once you get used to it personally, I feel is much easier to use. Follow the Chroot portion.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Good job on getting the script up it is confusing at first I know it was for me.;)


> Good job on getting the script up it is confusing at first I know it was for me thanks i cheated i went to the folder where i downloaded it clicked open this foilder in a terminal then copy and pasted the name of the file after sudo bash in terminal  .... im not great with the terminal but i cheat really well haha 

I'm away from home it'll be a while till i can get back to that computer but i'll give that a try and let you know the out come ... thanks again for the help ..

---

### Post by wilee-nilee on 2010-11-10
> **h4xor66 said:**
> thanks i cheated i went to the folder where i downloaded it clicked open this foilder in a terminal then copy and pasted the name of the file after sudo bash in terminal  .... im not great with the terminal but i cheat really well haha 

I'm away from home it'll be a while till i can get back to that computer but i'll give that a try and let you know the out come ... thanks again for the help ..

Thats not cheating, your thinking creatively.;)

---

### Post by h4xor66 on 2010-11-10
well that did the trick ...... 



> **wilee-nilee said:**
> 
once you get used to it personally, I feel is much easier to use.  after rebooting i went looking for the menu.lst file to see how it was configured ... there is none, i figured out that it was replaced with grub.cfg... that does NOT look easier to manually edit then legacy ... in fact it doesn't look like it can be edited .. it looks like if os-prober can't find the OS you're just out of luck ... i really hate change i spend a lot of time trying to commit all this stuff to memory then they go and change it on me ..... i'm probably not the right person to be using linux at all :P


thanks for all your help i really appreciate it .. i learned a lot about grub ... more then i ever really wanted to know actually haha



by the way you should tell people that the right way to run that script is to CD into the directory that it is in then enter code ```
sudo bash boot_info_script055.download
```

---

### Post by wilee-nilee on 2010-11-10
> **h4xor66 said:**
> well that did the trick ...... 



  after rebooting i went looking for the menu.lst file to see how it was configured ... there is none, i figured out that it was replaced with grub.cfg... that does NOT look easier to manually edit then legacy ... in fact it doesn't look like it can be edited .. it looks like if os-prober can't find the OS you're just out of luck ... i really hate change i spend a lot of time trying to commit all this stuff to memory then they go and change it on me ..... i'm probably not the right person to be using linux at all :P


thanks for all your help i really appreciate it .. i learned a lot about grub ... more then i ever really wanted to know actually haha

It seems un-editable but it is quite easy once you know whats up. The biggest advantage of grub2 for me has been that I have yet to do a install that it didn't find automatically.

Take a look at the links in that chroot link in drs305 signature.

---

### Post by h4xor66 on 2010-11-11
> **wilee-nilee said:**
> 
Take a look at the links in that chroot link in drs305 signature.

Ah ... i honestly didn't even see those little links before ... lots of good info there

---

