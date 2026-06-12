---
title: "boot menu help"
date: 2006-04-22
forum: General Help
---

### Post by sbddude on 2006-04-22
I need help setting up the boot menu to make windows the default. I tried the instructions that tell me to edit menu.lst, but there was no such file. Creating it did not help either. Please help!

I am booting from sdb. sda is my work hard drive and cannot be touched. 
Here is my fdisk -l:


Disk /dev/sda: 60.0 GB, 60011642880 bytes
240 heads, 63 sectors/track, 7752 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7751    58597528+   7  HPFS/NTFS

Disk /dev/sdb: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1959    15735636    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2            1960        6528    36700492+   7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sdb3            6529        6541      104422+  83  Linux
/dev/sdb4            6542        7296     6064537+   5  Extended
/dev/sdb5            6542        7296     6064506   8e  Linux LVM

---

### Post by Sandlst on 2006-04-22
Are you certain you entered the correct path to the grub menu? ```
sudo gedit /boot/grub/menu.lst
``` Just making sure.

---

### Post by sbddude on 2006-04-22
Yes. before I created the file. There was no such file there. THe grub directory was not there either. /boot was empty.

---

### Post by sbddude on 2006-04-24
Please help, I have not solved this problem.

---

### Post by cosmoshell on 2006-04-24
[QUOTE=sbddude]Please help, I have not solved this problem.[/QUOTE]
are you trying to acces that from windows?

---

### Post by solarwind on 2006-04-24
Hmm..

Open up a terminal and enter the following commands: (each line is one command)

------------------------------
cd /
sudo find -name menu.lst
-------------------------------

tell us what you get.

P.S.

This is a find command to find menu.lst, be patient, it may take some time.

---

### Post by sbddude on 2006-04-29
./boot/grub/menu.lst
./usr/share/doc/grub/examples/menu.lst
./home/menu.lst
find: WARNING: Hard disk link count is wrong for ./proc: this may be a bug in your filesystem driver. Automatically turning on find's -noleaf option. Earlier results may have filed to include directoris that should have been searched.

---

### Post by sbddude on 2006-05-20
Please help. I still am unable to change my default boot option.

---

### Post by adamkane on 2006-05-20
The file exists.

You should delete /home/menu.lst
```

cd /home
rm menu.lst

``` 
Edit /boot/grub/menu.lst
```

sudo gedit /boot/grub/menu.lst

``` 
It should look something like this:

> 
[FONT=Courier New]# menu.lst - See: grub(8), info grub, update-grub[/FONT][FONT=Courier New](8)[/FONT]
[FONT=Courier New] #            grub-install[/FONT][FONT=Courier New](8)[/FONT][FONT=Courier New] grub-floppy[/FONT][FONT=Courier New](8)[/FONT][FONT=Courier New],
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=/dev/hda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title        Ubuntu, kernel 2.6.15-23-686
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.15-23-686 root=/dev/hda2 ro quiet splash
initrd        /boot/initrd.img-2.6.15-23-686
savedefault
boot

title        Ubuntu, kernel 2.6.15-23-686 (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.15-23-686 root=/dev/hda2 ro single
initrd        /boot/initrd.img-2.6.15-23-686
boot

title        Ubuntu, kernel 2.6.15-23-386
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro quiet splash
initrd        /boot/initrd.img-2.6.15-23-386
savedefault
boot

title        Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro single
initrd        /boot/initrd.img-2.6.15-23-386
boot

title        Ubuntu, memtest86+
root        (hd0,1)
kernel        /boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1[/FONT]
 

Save and close the file.

Yes, I dual-boot. I'm so ashamed. My mama made me do it!

---

### Post by sbddude on 2006-05-20
Thanks for the quick reply. I tried your suggestion, but the changes to the file are not being applied. I made the default 3 and changed the timeout to 5 seconds. It still defaulted to unbuntu and had a 10 sec timer.

---

### Post by adamkane on 2006-05-20
It probably has to do with you using SCSI or SATA. I use EIDE, so you may have to change hd0,0 and hd0,1 to something else.

---

### Post by confused57 on 2006-05-20
[QUOTE=sbddude]Thanks for the quick reply. I tried your suggestion, but the changes to the file are not being applied. I made the default 3 and changed the timeout to 5 seconds. It still defaulted to unbuntu and had a 10 sec timer.[/QUOTE]

Sorry to jump in on this thread, but did it give you an option to save changes when you exited menu.lst?
I'm pretty new at this also, but look at adamkane's menu.lst:

1.)If he wanted to boot into windows, his default value would be 5; the first Ubuntu boot option kernel is 0, next is 1, & so on(the window's entry is actually the 6th, but Grub numbers  it as the 5th for the default).

2.)Your windows root path would probably be (hd1,0), which means windows would be found on hd#2, on partion#1.  sdb is actually hd1 in Grub 

Hope this helps & you can save changes...no guarantees it'll work.

Thanks aysiu, learn something new every day...

---

### Post by aysiu on 2006-05-20
[QUOTE=confused57]
1.)If he wanted to boot into windows, his default value would be 5; the first Ubuntu boot option kernel is 0, next is 1, & so on(the window's entry is actually the 6th, but Grub numbers  it as the 5th for the default).[/quote] It may actually be 6 because I believe this counts as a number: ```
# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root
``` Basically, anything that starts with *title* is an entry.

---

