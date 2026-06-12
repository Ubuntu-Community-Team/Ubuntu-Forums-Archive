---
title: "Can't boot into windows now."
date: 2006-06-02
forum: General Help
---

### Post by King Blah on 2006-06-02
Not long ago I installed Kubuntu. I have a windows partition now as well as the linux ones on this hard drive.
When I start the computer, the "GRUB" loader screen appears. It has three Ubuntu options (normal, safe mode or something and memtest something), and my Microsoft Windows XP professional one.
When I go to boot to my Windows XP one, i get the following:
```

Root (hd0,0)
Filesystem type unknown, partition type 0x7
save default
makeactive
chainloader +1
```
I am really worried I'll never be able to access windows again. All the files and folders are still intact as I can still access them from here. 

How do I fix this? I'm really new to linux. Also my windows xp partition is NTFS.

Edit: Argh. I have the feeling no one will be replying to this. At least can someon reply to this: How do I completely remove this GRUB and Kubuntu? I don't want it on my system anymore as it just seems to be creating problems. Hopefully then I'll be able to access my Windows XP partition..

---

### Post by givré on 2006-06-02
Post here your /boot/grub/menu.lst (gedit /boot/grub/menu.lst in a terminal)
and the result of df in a terminal (just type df)

---

### Post by King Blah on 2006-06-02
This is menu.lst:

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		3

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
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/sda2 ro

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

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```




This is df:
```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda2             18943504   1929364  16051848  11% /
varrun                  518048        80    517968   1% /var/run
varlock                 518048         4    518044   1% /var/lock
udev                    518048       156    517892   1% /dev
devshm                  518048         0    518048   0% /dev/shm
lrm                     518048     18856    499192   4% /lib/modules/2.6.15-23-386/volatile
/dev/sda1            140409752  85751928  54657824  62% /media/sda1
/dev/hdc               2825140   2825140         0 100% /media/cdrom0
```

---

### Post by givré on 2006-06-02
Argh, i can't really say whats wrong.
It seems that your windows is on /dev/sda1 so (hd0,0) should be okay. No idea

Anyone can help ?

---

### Post by givré on 2006-06-02
Just a try.

Whith my laptop, i had to delete the savedefault line to boot properly (don't really know why, if someone know...).

So try to delete this line from your windows boot command :
```
sudo gedit /boot/grub/menu.lst
```
And at the end of the file just delete savedefault to make it like that:
```
title		Microsoft Windows XP Professional
root		(hd0,0)
makeactive
chainloader	+1
```

---

### Post by King Blah on 2006-06-02
If i completely uninstalled grub/kubuntu would that help? If that's even possible

Edit: I'll try what you just mentioned above

---

### Post by King Blah on 2006-06-02
When I try to save I get an error that I need the right privileges or something. How do I save with administrator privileges?

Edit: Ah, I had to use the terminal. I use kubuntu so i had to use kate instead.

---

### Post by givré on 2006-06-02
Of course, because in linux when you are a simple user you can't do things that could break your system (it's why it is safer than windows)

So to run an application with root privilege, you have to type sudo before (Super Utilisateur DO).

In a terminal, just type :
```
sudo gedit /boot/grub/menu.lst
```
type your password, and you will be able to change what you want (be carefull to change only what i say, or it will break your system)

---

### Post by King Blah on 2006-06-02
Thanks. I tried doing what you said and I still get the same Filesystem type unknown error when trying to boot to windows. Looks like yet another windows installation ruined from linux... Arghhhh!!!!!!!!!!!!!

---

### Post by givré on 2006-06-02
[QUOTE=King Blah]I use kubuntu so i had to use kate instead.[/QUOTE]
oh yes, sorry for that ;)

---

### Post by nixt on 2006-06-02
Did accessing your Windows XP installation from grub ever work? Don't give up!

---

### Post by King Blah on 2006-06-02
I installed Kubuntu earlier today. I didn't reboot until earlier, when I tried to access windows, and I got the error. So no, accessing Windows from grub never worked.

---

### Post by King Blah on 2006-06-02
Is there anyway to bypass grub and just boot straight into windows Xp, ignoring it completely?

---

### Post by givré on 2006-06-02
[QUOTE=King Blah]If i completely uninstalled grub/kubuntu would that help? If that's even possible
[/QUOTE]

Not really. To rescue it, you should reinstall your mbr with a windows CD.

---

### Post by King Blah on 2006-06-02
How do I do that? Will I keep all my data?

---

### Post by nixt on 2006-06-02
Could you do a 

sudo fdisk -l /dev/sda ?

---

### Post by givré on 2006-06-02
It's a long time i didn't touch a windows cd, so i can't really help you, but i'm quite sure it's possible.
Just have a look at the option you have when you boot on your windows CD.

But you should try linux an other time, it's going better and better.

EDIT: try nixt thing before ;)

---

### Post by nixt on 2006-06-02
You can get windows to boot again definitely, but its best to get grub working... otherwise you'll never see kubuntu

---

### Post by King Blah on 2006-06-02
Here is the thing nixt said to do:
```
Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       17481   140413855    7  HPFS/NTFS
/dev/sda2           17482       19877    19245870   83  Linux
/dev/sda3           19878       19929      417690   82  Linux swap / Solaris

```

---

### Post by nixt on 2006-06-02
Are your familiar with your system BIOS? The one where you press the Delete when your system comes on?

Switch your hard drive to LBA mode, if it isnt already.

---

### Post by King Blah on 2006-06-02
I'll try and see if i can do that.

---

### Post by RavenOfOdin on 2006-06-02
[QUOTE=King Blah]I'll try and see if i can do that.[/QUOTE]

Just so you know, the majority of hard drives out nowadays are LBA.  That goes for anything above 8 GB.

---

### Post by King Blah on 2006-06-02
I don't know what LBA is, but in my bios the only setting my hard drive seemed to have was "Access"
I can set it to Auto or Large. It is currently on Auto by default

---

### Post by nixt on 2006-06-02
Try not to use automatic drive parameters too... use definite numbers that the BIOS recommends.

---

### Post by nixt on 2006-06-02
Try setting to LARGE

---

### Post by King Blah on 2006-06-02
Is this a miracle? The message flashed up briefly (the one i was getting before) but then Windows XP started loading!
An immense thankyou for all your help. I'll post back if I get any problems.
Once again thanks guys!

---

### Post by nixt on 2006-06-02
No problem and have fun!

---

### Post by King Blah on 2006-06-02
So far so good, it seems. If I ever wanted to uninstall kubuntu (to free up the disk space for example) is this easy to do?

Edit: Windows seems to be running quite slow. That "LARGE" setting or anything else wouldn't affect this, would it?

---

### Post by nixt on 2006-06-02
You could delete the linux partitions outright, but you would have to restore the master boot record (easy to do with a boot disk), so the computer boots generically again (since if you remove the linux partitions GRUB would go missing)

---

### Post by King Blah on 2006-06-02
[QUOTE=nixt]You could delete the linux partitions outright, but you would have to restore the master boot record, so the computer boots generically again (since if you remove the linux partitions GRUB would go missing)[/QUOTE]

Alright. Is restoring the MBR a risky process? Would I lose my data?

---

### Post by nixt on 2006-06-02
Probably the same amount of risk you took with installing kubuntu.

I'm not quite sure why Windows would load slower, but give it a few more reboots and see if this persists. Sometimes it needs to get used to new device settings, etc.

---

### Post by King Blah on 2006-06-02
Windows is loading fine now. It said something about installing a new device, which may have been from setting LARGE in the bios.

Thanks for the help once again!

---

### Post by linuchsan on 2006-06-02
start from a dos boot floppy with fdisk.
run fdisk /mbr and grub is gone
reboot in you windows system again

---

### Post by mostwanted on 2006-06-02
Man, I love these support success stories. Almost brings a tear to my eye :)

And King Blah: you're a very good new user. Patience is rewarded as was just exemplified.

---

