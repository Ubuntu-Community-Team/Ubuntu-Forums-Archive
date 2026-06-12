---
title: "Grub Error 17"
date: 2009-08-24
forum: General Help
---

### Post by pspkiller91 on 2009-08-24
Before we begin I know there are already many threads on this topic but none have helped me so far.

I decided to reorganise the partitions on my laptop's 250GB hard drive this morning. I booted a 9.04 Live CD, opened up GParted and proceeded to organise. I've gone from:

30GB NTFS primary (empty, unfinished project) + 15GB NTFS primary (empty, ditto) + 15GB Extended comprising of 14GB logical (Ubuntu) and 1GB Swap + Everthing else FAT32 (storage)

As you can probably see it was a mess. I therefore decided to change it to:
33GB Extended comprising of 30GB Ubuntu and 3GB Swap + 
30GB NTFS (will eventually be XP, needed for school) + Everything else (storage)

To do this I deleted the two empty NTFS partitions, moved the extended partition to the beginning of the disk and resised it to 33GB. I then resised its contained partitions to 30GB and 3GB respectively. I then created a 30GB NTFS partition in the empty space between the extended partition at the start and the storage partition at the end. I then resized the storage partition to fill the small gap that was left at the end of the 30GB NTFS partition.

Make sense?

Here is a graphical (read: doodle) representation of before and after. I hope you can make sense of it.
[IMG]http://i484.photobucket.com/albums/rr209/pspkiller_awesome/DSC01837.jpg[/IMG]
[IMG]http://i484.photobucket.com/albums/rr209/pspkiller_awesome/DSC01836.jpg[/IMG]

Better?


Anyway. To business.

GParted reproted to me that all operations had been completed successfully. I breathed a sigh of relief (everything is backed up anyway) and restarted. 

GRUB Error 17. I was half expecting a problem with GRUB but I thought that it was no biggie. I could always enter GRUB's menu and reconfigure, right? Erm, no. No prompt to hit ESC. Just a big, fat error message staring me in the face. 

So, pop the Live CD back in, get online and look for some help. [This guide (click) ]("http://stringofthoughts.wordpress.com/2009/05/24/grub-error-17-debianubuntu/")proved reasonably useful up until the point where it asks me to re-install GRUB. This is as far as I got:

```

sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> root (hd0,5)
root (hd0,5)
grub> setup (hd0)
setup (hd0)

Error 17: Cannot mount selected partition

```FYI: The partition that Ubuntu is currently installed on is sda5 and the Swap is sda6.

This is where I fall down. I know next to nothing about GRUB and the way it works. This is where I need your help.

Thanks.

---

### Post by P4man on 2009-08-24
sda5 would be hd(0,4) to grub. Grub starts counting at zero.
If you're unsure, in grub type:

find /boot/grub/stage1

and it will return on which hd(x,y) it finds a bootable kernel. Probably hd(0,4)

lol @ the pics btw!!

---

### Post by louieb on 2009-08-24
> **pspkiller91 said:**
> 
[/code]FYI: The partition that Ubuntu is currently installed on is sda5 and the Swap is sda6.

Are you sure? at the grub> what does this return?
```
find /boot/grub/stage2 

```If still not solved please follow the [Boot Info Script Instructions]("http://ubuntuforums.org/showpost.php?p=6725571&postcount=3") and put the results.txt file  in your next post (its long - used code tags)

lol P4man - did not see your post - great minds think alike

---

### Post by muteXe on 2009-08-24
I'm gonna take a screenshot of one of your pics, set it as my desktop background and see if i can convince my boss I'm defragging my work machine....

---

### Post by pspkiller91 on 2009-08-24
> **muteXe said:**
> I'm gonna take a screenshot of one of your pics, set it as my desktop background and see if i can convince my boss I'm defragging my work machine....

That good is it?

@P4man, Thanks! Dunno why I didn't spot that. Seems pretty obvious now that I see it. All is fixed and working now. But for how long I don't know. XP is going onto the empty partition in a few minutes time. WINE is good but it just can't cope with some of the music production apps I use for school (mostly Cubase). Seems a shame to install XP simply for a handful of programs. 

I'll report back on how things go.

---

### Post by P4man on 2009-08-24
> **pspkiller91 said:**
> But for how long I don't know. XP is going onto the empty partition in a few minutes time.

Then in a few minutes ubuntu will no longer boot :) Windows will overwrite grub with its own bootloader, which can't boot linux. You'll have to repeat the process to reinstall grub, but it will probably pick up your windows and add it to the menu. If not, we'll talk you through it, thats easy enough.

---

### Post by pspkiller91 on 2009-08-25
I've managed to get GRUB installed and working again. One problem though. At the menu there are multiple entries for Ubuntu and Ubuntu Safe Mode. Looking at the GRUB coinfiguration file I have this:

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
timeout        3

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
# kopt=root=UUID=f22a28dc-66d3-4dad-9450-9ef58100290a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f22a28dc-66d3-4dad-9450-9ef58100290a

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

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        f22a28dc-66d3-4dad-9450-9ef58100290a
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=f22a28dc-66d3-4dad-9450-9ef58100290a ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        f22a28dc-66d3-4dad-9450-9ef58100290a
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=f22a28dc-66d3-4dad-9450-9ef58100290a ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-14-generic
uuid        f22a28dc-66d3-4dad-9450-9ef58100290a
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=f22a28dc-66d3-4dad-9450-9ef58100290a ro quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid        f22a28dc-66d3-4dad-9450-9ef58100290a
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=f22a28dc-66d3-4dad-9450-9ef58100290a ro  single
initrd        /boot/initrd.img-2.6.28-14-generic

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        f22a28dc-66d3-4dad-9450-9ef58100290a
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=f22a28dc-66d3-4dad-9450-9ef58100290a ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        f22a28dc-66d3-4dad-9450-9ef58100290a
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=f22a28dc-66d3-4dad-9450-9ef58100290a ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        f22a28dc-66d3-4dad-9450-9ef58100290a
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=f22a28dc-66d3-4dad-9450-9ef58100290a ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        f22a28dc-66d3-4dad-9450-9ef58100290a
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=f22a28dc-66d3-4dad-9450-9ef58100290a ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        f22a28dc-66d3-4dad-9450-9ef58100290a
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Windows XP Professional
root (hd0,1)
makeactive
chainloader +1 

```

Is it safe to simply delete all the duplicate entries? As far as I can see they're all identical and therefore it should be fine. But as I've already said I know next to nothing about GRUB and its inner workings...

Also is it possible to re-order the entries so that XP is after Ubuntu and before Safe Mode and memtest86+? Instinct tells me that i should just move it into said location in the config file but I've noticed that all the other entries are within the "DEBIAN AUTOMAGIC KERNELS LIST" whatever that is. I'm guessing that XP isn't a Debian Automagic Kernel so I porbably cant put it there. Can I?

---

