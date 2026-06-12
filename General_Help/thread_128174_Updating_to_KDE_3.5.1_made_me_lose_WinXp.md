---
title: "Updating to KDE 3.5.1 made me lose WinXp"
date: 2006-02-10
forum: General Help
---

### Post by Zach1188 on 2006-02-10
I just updated to KDE 3.5.1, and now my WinXp is not in the MBR. It is still on the hard drive, with no harm done to the partition, it just does not have any way to boot. Before this happened, this is how my boot menu was set up:

[COLOR="Red"]Linux (Kubuntu, Standard)
Windows Xp Media Center Edition
_______________
Linux (Kubuntu, Recovery Mode)
Linux (Kubuntu, Memory Test)[/COLOR]

Obviously, I re-arranged it/renamed some things to the way I like it. 

Now, after updating KDE, it looks like this:

[COLOR="Red"]Ubuntu, kernel 2.6.12-10-386 
Ubuntu, kernel 2.6.12-10-386 (recovery mode)
Ubuntu, kernel 2.6.12-9-386 
Ubuntu, kernel 2.6.12-9-386 (recovery mode)
Ubuntu, memtest86+
________________________
Linux (Recovery Mode, Kubuntu)
Linux (Memory Test, Kubuntu)[/COLOR]


Other information:
I updated it using this instructions from:[http://ubuntuforums.org/showthread.php?t=126113&highlight=KDE+update]("http://ubuntuforums.org/showthread.php?t=126113&highlight=KDE+update"), using posts 2 and 4.

I am running on a Dell Inspiron 9300 (If this is relavent)

WinXp is on my second partion

Kubuntu is on my 5th partition

Swap Space is on my 6th partition (Virtual Memory)

Partitions 1 and 3 are taken by Dell Recovery (Or at leaste one is, unsure of the other)

Partions 5 and 6 are in an extended partion (Partition 4)

---

### Post by Jucato on 2006-02-10
Ok, some clarifications first.
1. MBR cannot affected by any upgrade. The only way to affect MBR is to directly modify it, which is a more complicated process than just upgrading.
2. GRUB, the bootloader, was the one that was modified. A bootloader is a software so it's far easier to correct. GRUB is responsible for displaying the menu that you see on startup to choose which you want to boot first.
3. Upgrading KDE should not normally modify GRUB, since it only modifies the Desktop Environment, which is a separate entity from the kernel.
4. Updating the kernel DOES modify GRUB because they are related to each other. Every time you update/install a kernel (or kernel image), your GRUB is updated to display these changes.

Guessing from the pieces of info you gave, somehow you updated your kernel as well as updating KDE. Your previous kernel was 2.6.12-9-386, while a 2.6.12-10-386 was newly installed, thus altering the menu. I'm sure your MBR is still intact, and that modifying GRUB's menu list will solve your problems.

Also, by default, Windows is put at the last of the menu.lst. You can change the order of the menus, but it will be overwritten when you update/install a kernel.

---

### Post by Zach1188 on 2006-02-10
Ok, I guess I got a little mixed up between GRUB/MBR, sorry, im still a noob.

ALL I did was what it said in posts 2 and 4, thats it. I entered the commands, let it download the updates, then rebooted my computer. Thats all. Once it turned back on, things got changed.

So how can I get WinXp back? I only have one hard drive, and it is on partition 2. I tried adding it my self, but I do not know what parameters it needs to find it.

---

### Post by Jucato on 2006-02-10
Ok, now I see your problem. Btw, no need to say sorry. Everyone was a newbie once. I'm a bit new, too (2 month old in Ubuntu). Ok, here goes my explanation:

You did a dist-upgrade, which upgrades your whole distro to whatever is the latest version available from the repositories. And the latest available kernel version (for Ubuntu family) is 2.6.12-10. I guess that you didn't upgrade your kernel ever since you installed Ubuntu, that is why it only updated now, together with KDE. 

I'm not a total GRUB expert, but let me try. but first, can you post your /boot/grub/menu.lst so  that I can try to modify it to fit your system?

---

### Post by Zach1188 on 2006-02-10
Sure thing, hope code tags are acceptable.

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		300

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
# kopt=root=/dev/sda5 ro vga=771

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

#This is where I tried to add it manually
title		WinXp
root		(hd0,2)
makeactive
chainloader	+1
boot
#------------

title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/sda5 ro vga=771 quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/sda5 ro vga=771 single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda5 ro vga=771 quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda5 ro vga=771 single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		________________________
root

title		Linux (Recovery Mode, Kubuntu)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda5 ro vga=771 single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Linux (Memory Test, Kubuntu)
root		(hd0,4)
kernel		/boot/memtest86+.bin  
boot

```

Thats the entire thing.

---

### Post by Jucato on 2006-02-10
ok I think I see your problem. You said that Windows is in  your 2nd partition of the first (and only) hard drive, right?

Your menu.lst lists Windows as:
```
#This is where I tried to add it manually
title		WinXp
root		(hd0,2)
makeactive
chainloader	+1
boot
#------------
```

but (hd0,2) is the 3rd partition of the first drive. Try to change it to (hd0,1) and see what happens. :D

---

### Post by Zach1188 on 2006-02-10
Thanks!!

You made me feel stupid, it never crossed my mind that 0 = Part.1, 1 = Part. 2, etc.

I should have thought of that, as it now seems like common sense, lol. Then again, I have only been using linux for a week now.

---

### Post by Jucato on 2006-02-10
It's ok. It's not entirely the most intuitive thing to start counting from 0. but unfortunately, that's how computers work. (Thanks to a bit of programming background). Sorry if I made you feel stupid. But I'm sure you're not the only one who had that problem.

Welcome to the wonderful world of Linux, and of counting from 0's!! :D

---

### Post by Zach1188 on 2006-02-10
Actually, I have been programming in Visual Basic for about 3 months now (I know thats not long, but still), so I should have figured it out. Anyways, thanks again.

---

### Post by Jucato on 2006-02-10
Sure thing. Just tell us if it already worked. :D

---

