---
title: "Grub hangs at Stage1.5 (no errors)"
date: 2009-09-01
forum: General Help
---

### Post by pattersondm85 on 2009-09-01
Hello all,

I will give you a brief rundown on hardware and the issue I am having.

Hardware:
Asus motherboard (old)
AMD 2600+ CPU
some ram
crappy video card (will be headless server)
PCI SATA controller for SATA support (know works with Ubuntu used on different server just fine)
(1) 80gig IDE drive for OS
(1) 1TB SATA drive for media, etc

I install Ubuntu 9.04 from the Live CD with no problem. When I rebooted I was first prompted with this after the POST.

```
Grub loading Stage1.5
Grub loading, please wait...
```

Then it would just hang undefinability. I tried using this tutorial on reinstalling grub [http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351") with no such luck. I tried both the methods in the tutorial and each time it said it was successful but still would hang at Grub loading.

While in the live CD I can see that the OS is installed on /dev/sdb1 (the 80gig IDE drive) and the 1tb media drive connected to the SATA PCI card is /dev/sda1.  My gut feeling is it is trying to load or look for the OS on the /dev/sda1 rather then /dev/sdb1.

Some details of my Grub while booted into the LIVE CD
device map
```
ubuntu@ubuntu:~$cat /mnt/root/boot/grub/device.map
(hd0)   /dev/sda
(hd1)   /dev/sdb
```

menu.lst
```
ubuntu@ubuntu:~$ cat /mnt/root/boot/grub/menu.lst
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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

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
# kopt=root=UUID=4ecf84a7-160a-4894-9a38-db5d8177d83b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=4ecf84a7-160a-4894-9a38-db5d8177d83b

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		4ecf84a7-160a-4894-9a38-db5d8177d83b
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=4ecf84a7-160a-4894-9a38-db5d8177d83b ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		4ecf84a7-160a-4894-9a38-db5d8177d83b
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=4ecf84a7-160a-4894-9a38-db5d8177d83b ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		4ecf84a7-160a-4894-9a38-db5d8177d83b
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
ubuntu@ubuntu:~$ 
```

Please let me know if there is anything I can edit or change to get this working. I will continue to read what I can but figure this isn't the first time for this issue to occur. 

Thanks,
Devin

---

### Post by P4man on 2009-09-01
This link here:

[http://grub.enbug.org/GrubLegacy](http://grub.enbug.org/GrubLegacy)

suggests you have corrupt files in /boot/grub

It also provides instructions for fixing it, by booting from a live cd, and chroot into your installation.

Hope that helps.

---

### Post by 1ronlung on 2009-09-01
Or use [www.supergrubdisk.org](www.supergrubdisk.org)

It's saved me from many a peril

---

### Post by pattersondm85 on 2009-09-01
> **P4man said:**
> This link here:

[http://grub.enbug.org/GrubLegacy](http://grub.enbug.org/GrubLegacy)

suggests you have corrupt files in /boot/grub

It also provides instructions for fixing it, by booting from a live cd, and chroot into your installation.

Hope that helps.

I looked at that site before posting and didn't have much luck. It suggest that the /root and /boot are on two different partitions. Yet, I have /dev/sdb1 (ext3), /dev/sdb2 (extension), and /dev/sdb5 (swap).  Also, I don't have a grub.conf file in my grub folder. So I hit a wall and wasn't able to proceed.

Keep the ideas coming since I would love to get this working.

---

### Post by rcayea on 2009-09-01
If you have other hard drives I suggest simply disabling them first, either in BIOS or physically inside the case. I believe that would help.

---

### Post by pattersondm85 on 2009-09-01
> **rcayea said:**
> If you have other hard drives I suggest simply disabling them first, either in BIOS or physically inside the case. I believe that would help.

I know if I unplug my SATA drive it will let me boot but I need to be able boot with the drive plugged in. So, if reboot I would have to unplug drive till Ubuntu is loaded and then replug in drive and re-mount drives. That won't help since I reboot computer often and remotely. 

Any thoughts?

---

### Post by P4man on 2009-09-02
you have to reinstall grub, but after chroot-ing into your install.
You could use the link I gave above, just substiture the drives and mount points with your actual drives. Or use this:

[http://developer.spikesource.com/wiki/index.php/Article:Ubuntu_how_to_re-install_grub_using_chroot](http://developer.spikesource.com/wiki/index.php/Article:Ubuntu_how_to_re-install_grub_using_chroot)

replace sda5 in that example with sdb1

and replace

"grub> root **(hd0,4)** " with **hd (1,0)** (or whatever grub finds)

and replace

"grub> setup (hd0)" with hd(1).


All that said, how is your bios set? Is it set to boot the sata or pata drive first? I have seen BIOSs do weird things, and changing the boot order not changing the way grub counts the drives, so it might be as simple as setting the bios to boot from the other drive.

---

### Post by pattersondm85 on 2009-09-02
> **P4man said:**
> you have to reinstall grub, but after chroot-ing into your install.
You could use the link I gave above, just substiture the drives and mount points with your actual drives. Or use this:

[http://developer.spikesource.com/wiki/index.php/Article:Ubuntu_how_to_re-install_grub_using_chroot](http://developer.spikesource.com/wiki/index.php/Article:Ubuntu_how_to_re-install_grub_using_chroot)

replace sda5 in that example with sdb1

and replace

"grub> root **(hd0,4)** " with **hd (1,0)** (or whatever grub finds)

and replace

"grub> setup (hd0)" with hd(1).


All that said, how is your bios set? Is it set to boot the sata or pata drive first? I have seen BIOSs do weird things, and changing the boot order not changing the way grub counts the drives, so it might be as simple as setting the bios to boot from the other drive.

I did try the link you posted before, it didn't help to much. I will follow the new site you posted tonight when I get home. I wanted to post regarding my BIOS.  BIOS is set to book my C: drive first. I have a PCI SATA card to provide connection for my SATA 1tb drive. So to my knowledge BIOS is set properly. I have spent 30-45 minutes changing settings trying to get it to disable PCI slots while booting, or force it to book the IDE drive only. Thus far not had so much luck.

I know if I unplug the SATA drive Ubuntu will boot fine then I can plug it in and mount -a and the drive works. So something with the SATA card and SATA drive are my issues. I appreciate the help you guys are trying to provide. I have learned more about grub then I ever cared to know.

Do you think if I tried a different boot manager the issue might go aways? try Lilo or something? I rather not but if it solves the problem I will try it.

Thanks again,
Devin

---

### Post by pattersondm85 on 2009-09-02
P4man,

I followed the link you provided and subsituted my information and still got the same results. This issue is becoming a black hole of myistories. 

here is my output of re-installing grub.

```
grub> find /boot/grub/stage1
 (hd1,0)


grub> root (hd1,0)


grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd1) (hd1)1+17 p (hd1,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

grub> 
```

Reboot and still hangs at where it always does.....

---

### Post by P4man on 2009-09-03
I can only think it has something to do with how your bios orders your disks. Im guessing its numbering the sata drive before the pata drive, even if you set it to boot from the pata.

In your grub menu.lst you have a line that is commented out:

# groot=4ecf84a7-160a-4894-9a38-db5d8177d83b

check if the UUID matches your pata drive (run "blkid") and if does (edit: removed wrong instructions :) )


Either that, or your bios is not set to boot from the pata before the sata drive. Double and triple check.

---

### Post by egalvan on 2009-09-03
> **P4man said:**
> 

[B]In your grub menu.lst you have a line that is commented out:
[/B]
# groot=4ecf84a7-160a-4894-9a38-db5d8177d83b

check if the UUID matches your pata drive (run "blkid") and if does, **[COLOR="Red"]remove the # sign.[/COLOR]**


Removing the # is**[COLOR="Red"] NOT CORRECT.[/COLOR]**
Per the instructions in the menu.lst

[B]## DO NOT UNCOMMENT THEM, Just edit them to your needs
[/B]

Forum member 'caljohnsmith' (an absolute genius at solving boot problems) along with meifera (another genius) had a script called

boot_info_script32.sh

it's on Sourceforge, here...

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

you download it to your desktop, run it,
(it scans all available drives for specific files, and other info)

then upload the 'results.txt' file that it generates.

It will show where GRUB is hiding...

---

### Post by P4man on 2009-09-03
> **egalvan said:**
> Removing the # is**[COLOR="Red"] NOT CORRECT.[/COLOR]**
Per the instructions in the menu.lst

[B]## DO NOT UNCOMMENT THEM, Just edit them to your needs
[/B]

I stand corrected :)

---

### Post by pattersondm85 on 2009-09-03
P4man,

I will double and triple check those settings. What you said about the SATA and PATA is exactly what I have been thinking for a while. I will check again tonight. I have an older motherboard and I am about to throw that in the machine and just see if that works and if so call it good. But it is never fun to go back words regarding hardware age you are using.

Thanks,
Devin

---

### Post by P4man on 2009-09-03
there is no reason you should switch motherboards over this.
If it is indeed a bios thing, you should be able to work around it somehow, if no other way then installing grub on the sata drive and booting from there.

---

### Post by pattersondm85 on 2009-09-03
> **P4man said:**
> there is no reason you should switch motherboards over this.
If it is indeed a bios thing, you should be able to work around it somehow, if no other way then installing grub on the sata drive and booting from there.

I just want to make sure it is clear that the motherboard doesn't have any SATA connector. The SATA drive is connected through a SATA card connected to my PCI slot. So I am not sure if my BIOS would be able to boot from a drive connected to a SATA RAID card (PCI slot).

Any thoughts?

---

### Post by P4man on 2009-09-03
> **pattersondm85 said:**
> I just want to make sure it is clear that the motherboard doesn't have any SATA connector. The SATA drive is connected through a SATA card connected to my PCI slot. So I am not sure if my BIOS would be able to boot from a drive connected to a SATA RAID card (PCI slot).

Any thoughts?

aaaah. I must have missed that. Well. My only thought is that its most likely somehow related to your problem :)

does the sata card have its own bios where you can change stuff? You might want to poke around in there about boot order.

---

### Post by pattersondm85 on 2009-09-03
> **P4man said:**
> aaaah. I must have missed that. Well. My only thought is that its most likely somehow related to your problem :)

does the sata card have its own bios where you can change stuff? You might want to poke around in there about boot order.

It does have some options but it is a POS card if you know what I mean. I don't use it for raid features but just to give me SATA connectors. The only options the card gives me are to low level format, build a raid, repair raid, and thats it I think. 

Weird is I have used this card with a different mobo and had no issues. Thats why it is puzzling. 

I will try that script tonight if I get a chance. ty

---

### Post by Zoot7 on 2009-09-03
Quick suggestion.. :)

Have you tried the latest BIOS for that motherboard? 

Another thing that might be worth considering is the Hard Drive Detect Delay, if you've a setting for that it'd be worth a shot to fiddle with that. The fact that it boots fine minus one hard drive would lead me to that belief.

---

### Post by pattersondm85 on 2009-09-03
> **Zoot7 said:**
> Quick suggestion.. :)

Have you tried the latest BIOS for that motherboard? 

Another thing that might be worth considering is the Hard Drive Detect Delay, if you've a setting for that it'd be worth a shot to fiddle with that. The fact that it boots fine minus one hard drive would lead me to that belief.

Zoot7, I do believe it does have a HDD Detect Delay. I played within the past with little luck. I think it just delayed the drive which hold the MBR and Grub.  I would love to delay the SATA drive until Grub has booted successfully.  But I will doubt and triple check that setting tonight just to make sure.

ty,
devin

---

### Post by Zoot7 on 2009-09-03
I've a similar problem with my Gigabyte GA-MA790FXT-UD5P board except it's with the XP Bootloader. If I boot XP directly from the hard drive it's installed on, it works about 50% of the time, other times it'll lock up, but if I boot it from GRUB via the hard drive Ubuntu is installed on, it works 100% the time. Strange but since I'm using GRUB anyway it doesn't bother me too much.

Anyway, let us know how you get on.

---

