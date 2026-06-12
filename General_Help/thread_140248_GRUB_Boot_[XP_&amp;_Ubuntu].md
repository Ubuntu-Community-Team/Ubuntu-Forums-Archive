---
title: "GRUB Boot [XP &amp; Ubuntu]"
date: 2006-03-05
forum: General Help
---

### Post by WarAngel on 2006-03-05
Okay, here's my setup. I have one hard drive (master) with Ubuntu installed on it. Then I have a second hard drive (slave) with Windows XP installed on it. If I had my choice, I would just delete Windows XP and use that hard drive for extra storage. Unfortunatly, my dad likes Windows XP better and I cannot convince him to switch to Ubuntu due to incompatability with our printer on Ubuntu.

Anyway, I was wondering how I could setup GRUB to boot Windows XP from the second hard drive in the GRUB boot menu (reached by pressing 'esc' when GRUB first loads).

Thanks in advance for any help!

---

### Post by Sutekh on 2006-03-05
You will need to edit the GRUB menu

First do a backup
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
```
Then edit the file (you could use **gedit** instead of **nano**)
```
sudo nano /boot/grub/menu.lst
```
Once the file is open look for this line
```

default         0
```
Here is where you change the default GRUB option.  If you look further down the file you will find the entries for the boot options.  

Start counting from '0' and every time you see something like
```
title           Ubuntu Breezy, kernel 2.6.12-10-386

```
Count up one.

When you get to the Windows XP title use that number as the default.  Save the file (Ctrl-O), quit (Ctrl-X) and your done

---

### Post by lha on 2006-03-06
[QUOTE=WarAngel]Okay, here's my setup. I have one hard drive (master) with Ubuntu installed on it. Then I have a second hard drive (slave) with Windows XP installed on it. If I had my choice, I would just delete Windows XP and use that hard drive for extra storage. Unfortunatly, my dad likes Windows XP better and I cannot convince him to switch to Ubuntu due to incompatability with our printer on Ubuntu.

Anyway, I was wondering how I could setup GRUB to boot Windows XP from the second hard drive in the GRUB boot menu (reached by pressing 'esc' when GRUB first loads).

Thanks in advance for any help![/QUOTE]
Add these lines to the end of /boot/grub/menu.lst.
```
title           Windows
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1
```

---

### Post by bcaton on 2006-03-06
History: 2 pc's. This one with ubuntu, another with xp. Xp motherboard is now dead.Set xp hard drive  jumper to slave, installed physically, and followed the instructions. Xp drive is formatted in ntfs, with some valued data. I can live without it but I'd like to dual boot with current config if possible. Windows cd is lost, possibly stolen (long story) and i can't afford another one. I'd really like to avoid buying it anyway as i am told vista is coming out soon. Before someone gets political, i and my partner need windows for work etc.

menu.lst is below if it helps?

Grub seems to work but xp seems to fail after loading mups.sys. I've read a lot of different opinions about what to do. Some people say it's an issue with grub. Others say "swap the master and slave so that xp is the master" (I'll do that when my back is better but right now typing is all i can do). Others say it's a security measure. Xp has detected new hardware and auto destructed.  I don't know what to believe. 

I'm hoping to be able to fiddle when my back's better but meanwhilst I've installed everything to do with ntfs from snyaptic but being a novice, and can read the drive's contents (thanks to [http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)) so i can backup hopefully if i do have to reinstall. (*groan!*)

Can anyone tell me if there's something i needed to do in ubuntu to make xp bootable past the mups.sys file, or am i looking at a bug in windows (can't cope with being on a slave drive), or what? aaargh. So close and yet so far ;) 

Thanks!

Brett. 


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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

---

### Post by Vampire Palin on 2006-03-06
It’s not a problem with grub it a problem with Windows, unless the hard drive was from a computer with the same motherboard? It will try to load drive for the old one and give you that error. Even if you get it load you need to install the drivers for that motherboard and reactivate it "Windows see it as a new computer" and will likely be unstable. 

If you still have the CD Key for WinXP and if its OEM key a recovery cd from Dell, HP, Compaq Etc.. Will work if its the same version type i.e. SP1 SP2.. So ask a friend to see if you can use theirs. If it a retail CD you can get a new replacement from Microsoft for a small cost like (25.00) I think!!

So anyway you look at it your better off back up & reinstall it .

Please someone let me know if I am wrong.

Thanks,
	Palin

---

