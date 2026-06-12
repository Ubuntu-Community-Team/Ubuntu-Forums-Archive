---
title: "grub  boot-problem"
date: 2009-08-07
forum: General Help
---

### Post by davewickett on 2009-08-07
please help ive installed linux mint where sda1 was (vista) & now i can not boot again getting msg error 21 grub loading ive tryed adding bootloader to sda0.0 and to the main drive sda but just getting same msg each time its saying they are installed ok what can i do to get them to boot of a bootloader again please help this is all i need thanks
dave
[ATTACH]123988[/ATTACH]

---

### Post by merlinus on 2009-08-07
Try supergrub:

[http://supergrubdisk.org]("http://supergrubdisk")

---

### Post by davewickett on 2009-08-07
yes i do have supergrub disc put it on usb booted off it and not helping

the only way i could get round this b4 was installing my girlfriends vista discs off acer i have hp then ubuntu again like i say it all looks installed ok

---

### Post by merlinus on 2009-08-07
Run from the live cd, go to Places and click on Computer, and navigate to filesystem/media to see if and where your ubuntu partition is mounted.  It will probably be in /media/disk.

If so, then open a terminal and post results of

```
gksudo gedit /media/disk/boot/grub/menu.lst
```

If something other than /disk, change that in the above command.

---

### Post by davewickett on 2009-08-07
that is blank and the command is blank aswell

---

### Post by merlinus on 2009-08-07
Results of

```
sudo fdisk -l
```

---

### Post by davewickett on 2009-08-07
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb034d7e6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10975    88156656   83  Linux
/dev/sda2           29181       30401     9798656    7  HPFS/NTFS
/dev/sda3           10976       29180   146231662+   5  Extended
/dev/sda5           10976       28241   138689113+  83  Linux
/dev/sda6           28242       29180     7542486   82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$

---

### Post by merlinus on 2009-08-07
Did you click on Places/Computer?

If so, and it did not work as I outlined, then we can manually mount it. 

It seems from yuou screenshot that ubuntu is on sda5.  If so, then:

```
sudo mkdir /media/disk
sudo mount -t ext3 /dev/sda5 /media/disk
cat /media/disk/boot/grub/menu.lst
```

---

### Post by davewickett on 2009-08-07
ubuntu@ubuntu:~$ sudo mkdir /media/disk
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda5 /media/disk
ubuntu@ubuntu:~$ cat /media/disk/boot/grub/menu.lst
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
# kopt=root=UUID=7bda63c1-4efc-40ba-8e72-ceee67094585 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7bda63c1-4efc-40ba-8e72-ceee67094585

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

title        Ubuntu 9.04, kernel 2.6.28-14-generic
uuid        7bda63c1-4efc-40ba-8e72-ceee67094585
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=7bda63c1-4efc-40ba-8e72-ceee67094585 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid        7bda63c1-4efc-40ba-8e72-ceee67094585
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=7bda63c1-4efc-40ba-8e72-ceee67094585 ro  single
initrd        /boot/initrd.img-2.6.28-14-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        7bda63c1-4efc-40ba-8e72-ceee67094585
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=7bda63c1-4efc-40ba-8e72-ceee67094585 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        7bda63c1-4efc-40ba-8e72-ceee67094585
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=7bda63c1-4efc-40ba-8e72-ceee67094585 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        7bda63c1-4efc-40ba-8e72-ceee67094585
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title        Linux Mint 7 Gloria Universal, kernel 2.6.28-11-generic (on /dev/sda1)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=d4e87bc0-aeaa-47d7-a83b-630aa8f9b87a ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title        Linux Mint 7 Gloria Universal, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda1)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=d4e87bc0-aeaa-47d7-a83b-630aa8f9b87a ro single 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title        Linux Mint 7 Gloria Universal, memtest86+ (on /dev/sda1)
root        (hd0,0)
kernel        /boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
chainloader    +1

ubuntu@ubuntu:~$

---

### Post by davewickett on 2009-08-07
yes it is mounted when i go into there now but do i need to mount sda1 linux mint now as that is not mounted
or what do i do next

i can get up my menu.lst (disk) - gedit now aswell

---

### Post by merlinus on 2009-08-07
When you reboot after removing live cd, what comes up?  Do you see grub?  If so, what are your choices?

The entries in menu.lst look fine, so it must be something else.

---

### Post by davewickett on 2009-08-07
ill reboot now but like i said when i had vista installed and put ubuntu on it worked fine i tryed to put ubuntu on its own got the same msg so i had to put some vista disks on first then ubuntu again it was fine again now put linux on where vista was getting same msg again ill let you know what happens now thanks for trying to help me

---

### Post by davewickett on 2009-08-07
no when i try to boot it says  *Grub loading error* 21 and thats all that happens

---

### Post by Loosewheel on 2009-08-07
Hi davewickett,
Here are some links that will help:
[http://jbakshi.50webs.com/Linux_tutorial/GRUB/GNU%20GRUB%20simplified.html](http://jbakshi.50webs.com/Linux_tutorial/GRUB/GNU%20GRUB%20simplified.html)
[http://orgs.man.ac.uk/documentation/grub/grub_toc.html#SEC_Contents](http://orgs.man.ac.uk/documentation/grub/grub_toc.html#SEC_Contents)

If you reboot and hit 'Esc' as soon as you see "grub....", (I think it says 'loading'), that will give you a grub command line, (grub>).
Enter this command: configfile (hd0,4)/boot/grub/menu.lst, and see if the boot loader GUI comes up.

Take a look at "GRUB Rescue in three steps" in that first link.
BTW, you got to be quick with the 'Esc' key.

---

### Post by davewickett on 2009-08-07
> **Loosewheel said:**
> Hi davewickett,
Here are some links that will help:
[http://jbakshi.50webs.com/Linux_tutorial/GRUB/GNU%20GRUB%20simplified.html](http://jbakshi.50webs.com/Linux_tutorial/GRUB/GNU%20GRUB%20simplified.html)
[http://orgs.man.ac.uk/documentation/grub/grub_toc.html#SEC_Contents](http://orgs.man.ac.uk/documentation/grub/grub_toc.html#SEC_Contents)

If you reboot and hit 'Esc' as soon as you see "grub....", (I think it says 'loading'), that will give you a grub command line, (grub>).
Enter this command: configfile (hd0,4)/boot/grub/menu.lst, and see if the boot loader GUI comes up.

Take a look at "GRUB Rescue in three steps" in that first link.
BTW, you got to be quick with the 'Esc' key.


thanks ill have a look now but esc is to get up my boot order and stuff ill let you know if it worked when i read them links thanks

---

### Post by davewickett on 2009-08-07
still no joy if i press esc that  gives me my [I]bios settings i just dont know what to do
[/I]

---

### Post by Loosewheel on 2009-08-07
You have to wait until you see 'grub loading...' on the monitor.
(If you indeed get stage1 to run), after the 'post' is done.
If you do manage to get in, you'll see a menu list and options at the bottom.....
Press 'c' to get the command line.
Let me know if you're able to do that, because then you can use all the commands; Like
'find' and 'tab key' completion.

---

### Post by davewickett on 2009-08-09
> **Loosewheel said:**
> You have to wait until you see 'grub loading...' on the monitor.
(If you indeed get stage1 to run), after the 'post' is done.
If you do manage to get in, you'll see a menu list and options at the bottom.....
Press 'c' to get the command line.
Let me know if you're able to do that, because then you can use all the commands; Like
'find' and 'tab key' completion.


i get to stage 2 i think it said but ive just got vista & ubuntu installed again & gave 150gb to ubuntu & 80gb to vista im putting backtrack on usb to boot into aswell i did not want vista on my laptop as its so high maintaince i went to a shop & the man said its most likey because you have to have windows on it somewhere so the only way would be to daul-boot i did find it mad that i could not install any linux distro on my whole drive it said it was installed ok but just would not boot ive installed that many times now i have to give up & stick with this but thank you all for your help [ATTACH]124220[/ATTACH]

---

