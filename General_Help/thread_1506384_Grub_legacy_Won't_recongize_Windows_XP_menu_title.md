---
title: "Grub legacy Won't recongize Windows XP menu title"
date: 2010-06-10
forum: General Help
---

### Post by RusitoQbano on 2010-06-10
Hi guys,
I´ve been using jaunty for a year now, and cause I've worked around many issues, I do consider myself almost an experienced user. A couple of days ago after an update of the kernel I selected for the fierst time the option : "change boot menu as in update" as to see if there would be any changes when I boot to kernel 28-19.
 
But to my surprise what I saw afterwards was that the nicely set up and working dual boot configuration was gone. I had put it manually without problems into menu.lst, because I installed Windows after Ubuntu.
 
Now GRUB doesn't see 
 
title Windows
root (hd 0,0)
makeactive
chainloader +1
 
no matter where I put it. Neither before nor after the automagic kernel list nor inside it. It does see all the linux kernels I uncomment.
Windows just doesn't appear in the boot menu.
My partitions are just fine, XP is in sda1 where it loves to be and i can acces the partition from ubuntu without any problems.
To me it's just some kinda problem with menu.lst
 
PLZ help

---

### Post by RusitoQbano on 2010-06-10
Some how the Forum seems to ignore my request.
Please guys reply

---

### Post by RusitoQbano on 2010-06-10
Forgot to say:
The boot info script gives me a syntax error. bash doesn't seem to like it

---

### Post by confused57 on 2010-06-10
Download or move the bootinfo script to your Desktop, then just copy & paste the command for running it:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

If it still won't run, post the output of:
```
sudo fdisk -l
```
-l is a small "L"
and 
```
gedit /boot/grub/menu.lst
```

---

### Post by RusitoQbano on 2010-06-10
Here the output when running boot info script:

```
andy@andy-laptop:~$ cd Desktop
andy@andy-laptop:~/Desktop$ sudo bash boot_info_script055.sh
[sudo] password for andy: 
: command not found.sh: line 52: 
: command not found.sh: line 53: 
'oot_info_script055.sh: line 63: syntax error near unexpected token `
'oot_info_script055.sh: line 63: `fi 
andy@andy-laptop:~/Desktop$ 
```Output of fdisk -l

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x075b075b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825       15538    94092705    b  W95 FAT32
/dev/sda3           15539       19457    31479367+   5  Extended
/dev/sda5           15539       19290    30137908+  83  Linux
/dev/sda6           19291       19457     1341396   82  Linux swap / Solaris
```menu.lst:

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=ea525f27-efac-42f5-8068-49fa6bdbf0c0 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ea525f27-efac-42f5-8068-49fa6bdbf0c0

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

title        Ubuntu 9.04, kernel 2.6.28-19-generic
uuid        ea525f27-efac-42f5-8068-49fa6bdbf0c0
kernel        /boot/vmlinuz-2.6.28-19-generic root=UUID=ea525f27-efac-42f5-8068-49fa6bdbf0c0 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-19-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-19-generic (recovery mode)
uuid        ea525f27-efac-42f5-8068-49fa6bdbf0c0
kernel        /boot/vmlinuz-2.6.28-19-generic root=UUID=ea525f27-efac-42f5-8068-49fa6bdbf0c0 ro  single
initrd        /boot/initrd.img-2.6.28-19-generic

#title        Ubuntu 9.04, kernel 2.6.28-18-generic
#uuid        ea525f27-efac-42f5-8068-49fa6bdbf0c0
#kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=ea525f27-#efac-42f5-8068-49fa6bdbf0c0 ro quiet splash 
#initrd        /boot/initrd.img-2.6.28-18-generic
#quiet

#title        Ubuntu 9.04, kernel 2.6.28-18-generic (recovery mode)
#uuid        ea525f27-efac-42f5-8068-49fa6bdbf0c0
#kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=ea525f27-#efac-42f5-8068-49fa6bdbf0c0 ro  single
#initrd        /boot/initrd.img-2.6.28-18-generic

#title        Ubuntu 9.04, kernel 2.6.28-17-generic
#uuid        ea525f27-efac-42f5-8068-49fa6bdbf0c0
#kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=ea525f27-#efac-42f5-8068-49fa6bdbf0c0 ro quiet splash 
#initrd        /boot/initrd.img-2.6.28-17-generic
#quiet

#title        Ubuntu 9.04, kernel 2.6.28-17-generic (recovery mode)
#uuid        ea525f27-efac-42f5-8068-49fa6bdbf0c0
#kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=ea525f27-#efac-42f5-8068-49fa6bdbf0c0 ro  single
#initrd        /boot/initrd.img-2.6.28-17-generic

#title        Ubuntu 9.04, kernel 2.6.28-16-generic
#uuid        ea525f27-efac-42f5-8068-49fa6bdbf0c0
#kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=ea525f27-#efac-42f5-8068-49fa6bdbf0c0 ro quiet splash 
#initrd        /boot/initrd.img-2.6.28-16-generic
#quiet

#title        Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
#uuid        ea525f27-efac-42f5-8068-49fa6bdbf0c0
#kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=ea525f27-#efac-42f5-8068-49fa6bdbf0c0 ro  single
#initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        ea525f27-efac-42f5-8068-49fa6bdbf0c0
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=ea525f27-efac-42f5-8068-49fa6bdbf0c0 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        ea525f27-efac-42f5-8068-49fa6bdbf0c0
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=ea525f27-efac-42f5-8068-49fa6bdbf0c0 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

#title        Ubuntu 9.04, kernel 2.6.28-11-generic
#uuid        ea525f27-efac-42f5-8068-49fa6bdbf0c0
#kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=ea525f27-#efac-42f5-8068-49fa6bdbf0c0 ro quiet splash 
#initrd        /boot/initrd.img-2.6.28-11-generic
#quiet

#title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
#uuid        ea525f27-efac-42f5-8068-49fa6bdbf0c0
#kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=ea525f27-#efac-42f5-8068-49fa6bdbf0c0 ro  single
#initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        ea525f27-efac-42f5-8068-49fa6bdbf0c0
kernel        /boot/memtest86+.bin
quiet



### END DEBIAN AUTOMAGIC KERNELS LIST
title   Windows XP Professional
root   (hd0,0)
makeactive
chainloader   +1
```

---

### Post by RusitoQbano on 2010-06-10
Bump

---

### Post by WorMzy on 2010-06-10
Comment out a few of the other entries, see if that makes any difference.

---

### Post by RusitoQbano on 2010-06-10
The funny part is I tried uncommenting the Linux example option, and IT DID appear in the grub menu.
Also I put saved as default and a savedefault entry in my Windows option but grub booted to jaunty kernel 28-19 anyways
So my next quiestion is: Is there a way that Grub would ignore any non linux entry under any circumstance?

---

### Post by oldfred on 2010-06-10
But we have seen where it does not show because you have so many entries, if you scroll down it appears.

You can limit the number of kernels shown, change the all to 2. and run
sudo update-grub

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=[COLOR=Red]all[/COLOR]

---

### Post by confused57 on 2010-06-10
> **oldfred said:**
> But we have seen where it does not show because you have so many entries, if you scroll down it appears.

You can limit the number of kernels shown, change the all to 2. and run
sudo update-grub

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=[COLOR=Red]all[/COLOR]

Great observation, oldfred, I didn't see anything wrong with his menu.lst.  Believe
you nailed it.

---

### Post by RusitoQbano on 2010-06-10
Sorry to disappoint you guys but it didn't help.
Anyway, I found a stupid solution for this stupid problem:
I DELETED MENU.LST ALTOGETHER!!!
Then just run update-grub and it generates a new one. There there was again the example line for Windows which I uncommented and moved to the bottom.
I liked Freds idea about limiting the kernel lines, because they occupy space on the screen. Now I got myself a pretty neat boot menu again.
Sure it was some kinda stupid syntax error when I was fixing menu.lst manually like having one space/linebreak between the lines instead of 2/tab+line break Or maybe because I copied the windows line from an odt or doc file where I had tips about grub and it has different linebreaks.
What does bother me now is: why couldn't I run the boot info script and why does my pc freeze up when I try to boot from the live CD?
Any ideas?

---

### Post by RusitoQbano on 2010-06-10
Just for the info, my new menu.lst:
```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=ea525f27-efac-42f5-8068-49fa6bdbf0c0 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ea525f27-efac-42f5-8068-49fa6bdbf0c0

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
# howmany=2

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

title        Ubuntu 9.04, kernel 2.6.28-19-generic
uuid        ea525f27-efac-42f5-8068-49fa6bdbf0c0
kernel        /boot/vmlinuz-2.6.28-19-generic root=UUID=ea525f27-efac-42f5-8068-49fa6bdbf0c0 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-19-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-19-generic (recovery mode)
uuid        ea525f27-efac-42f5-8068-49fa6bdbf0c0
kernel        /boot/vmlinuz-2.6.28-19-generic root=UUID=ea525f27-efac-42f5-8068-49fa6bdbf0c0 ro  single
initrd        /boot/initrd.img-2.6.28-19-generic

title        Ubuntu 9.04, kernel 2.6.28-18-generic
uuid        ea525f27-efac-42f5-8068-49fa6bdbf0c0
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=ea525f27-efac-42f5-8068-49fa6bdbf0c0 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-18-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-18-generic (recovery mode)
uuid        ea525f27-efac-42f5-8068-49fa6bdbf0c0
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=ea525f27-efac-42f5-8068-49fa6bdbf0c0 ro  single
initrd        /boot/initrd.img-2.6.28-18-generic

title        Ubuntu 9.04, memtest86+
uuid        ea525f27-efac-42f5-8068-49fa6bdbf0c0
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title        Windows XP Professional
 root        (hd0,0)
 makeactive
 chainloader    +1
```

---

### Post by oldfred on 2010-06-10
Things like hidden tabs or LF or CR can cause all sorts of issues that are just about impossible to fix except the way you did by starting over.

I think when you download the boot info script to a working install it now goes into Downloads and you have to run it from there. The instructions are more oriented to using the liveCD.

I did this. I use ls to confirm that I am typing a file or directory with correct capitalization. And I use tab to complete a command like the name - I typed boot_  then hit tab and it completed.

List from my history:
501  ls
  502  cd Downloads
  503  ls boo*
  504  sudo bash boot_info_script055.sh 
  505  history
fred@fred-desktop:~/Downloads$

---

### Post by confused57 on 2010-06-11
> **RusitoQbano said:**
> Sorry to disappoint you guys but it didn't help.
Anyway, I found a stupid solution for this stupid problem:
I DELETED MENU.LST ALTOGETHER!!!
Then just run update-grub and it generates a new one. There there was again the example line for Windows which I uncommented and moved to the bottom.
I liked Freds idea about limiting the kernel lines, because they occupy space on the screen. Now I got myself a pretty neat boot menu again.
Sure it was some kinda stupid syntax error when I was fixing menu.lst manually like having one space/linebreak between the lines instead of 2/tab+line break Or maybe because I copied the windows line from an odt or doc file where I had tips about grub and it has different linebreaks.
What does bother me now is: why couldn't I run the boot info script and why does my pc freeze up when I try to boot from the live CD?
Any ideas?

I think it might have been due to the fact you didn't leave a space between ###BEGIN...LIST and the Windows title, as in your original menu.lst:
```
### END DEBIAN AUTOMAGIC KERNELS LIST
title   Windows XP Professional
root   (hd0,0)
makeactive
chainloader   +1
```

Good job getting it working.

---

