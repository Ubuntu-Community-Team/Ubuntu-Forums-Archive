---
title: "Is there any hope for my computer?"
date: 2010-02-01
forum: General Help
---

### Post by pojr on 2010-02-01
I have the latest version of Ubuntu, and I recently downloaded it (maybe like two months ago), and I've been having many problems with it. Here are the issues:

To start, I can't start my computer up. It's a Toshiba laptop that used to run on Windows XP. Not sure if that matters. Anyway, it goes to this screen that says "Starting up..." and it never leaves that screen. Seriously I had it up for a half an hour, and it remained there.

When I hit ESC at the top left of my keyboard, I'm prompted to multiple boot variations, and when I hit one of those, occasionally it starts up, occasionally it doesn't. Here are some pictures:

[**Computer information.**](http://imgh.us/676A0031.jpg)


[**The result of letting the computer start up.**](http://imgh.us/676A0032.jpg)

[**The result when the boot menu is prompted.**](http://imgh.us/676A0033.jpg)

[color=red]**Sorry, I don't know how to resize these pictures.**[/color]

Mainly focus on the last picture. I can select any of those options. Here's what happens for each:

**Kernel 2.6.31-16 generic:** Loads "Starting up..."

**Kernel 2.6.31-14 generic:** Used to load up Ubuntu to my desktop like it should, except without any volume, and the special effects don't work. Now it just loads "Starting up..."

**Kernel 2.6.28-16 generic:** Loads up Ubuntu to my desktop like it should, except without any volume, and the special effects don't work.

**Kernel 2.6.27-15 generic:** Lots of garbage text, at least I think. I can't remember.

**Kernel 2.6.24-19 generic:** Loads "Starting up..."

The recovery modes simply load up garbage text. Anyway, how do I fix this? Is there a way? I'm not sure why this happenes, but ever since I upgraded, I immediately started having these problems. I think that maybe my computer cannot handle the full glory of the latest Ubuntu. I assure you that the version before 9.10 worked perfect.

---

### Post by Iowan on 2010-02-01
Unfortunately, your pix didn't attach.

---

### Post by M1GEO on 2010-02-01
When you say load up a load of garbage text in recovery mode, how do you mean?  Do you get random characters or do you get the kernel messages (words, but maybe meaningless to the unsuspecting?)

If you get the kernel log, what does it mention as the last few things?

You say it boots up sometimes?  Do you get a graphical interface?  Do you have any external hardware connected?  If so, try to remove it all.  This is especially true for USB drives, and SD cards.  These may hang the system as it tries to mount/enumerate the device.

A little more information.  Also, your images did attach, they are just *very* large.

---

### Post by NightwishFan on 2010-02-01
You should add the images as uploads or links when you are posting, that way they thumbnail or are external.

---

### Post by jamesisin on 2010-02-01
Agreed.

I can't read your post with these huge images torquing the page layout.

Edit your original post and choose Go Advanced.  You can use the paper clip icon in the buttons bar above the text block for attaching your images.

---

### Post by Leppie on 2010-02-01
have you ever done a memtest?

---

### Post by Greenbean209 on 2010-02-01
Did your installation work properly before. You mention you downloaded the newest ubuntu. Do you mean you upgraded and this happened?

---

### Post by houseworkshy on 2010-02-01
It looks like a software problem rather than hardware so yes there is probably hope.  On the one which works but doesn't have destop effects try installing the hardware drivers again.  In the rescue mode they are automatically disabled.  You also say "occasionally" which does sound like hardware.  Could be overheating in which case a good clean inside the box can work wonders.

---

### Post by pojr on 2010-02-04
Sorry about the huge pictures. I took them on my cell phone, and I couldn't figure out how to resize them. I'll change them to clickable URLs. Anyway, Yeah, I meant to say that I upgraded from 9.04. When I upgraded, I was immediately faced with this problem, which is weird, because 9.04 worked absolutely perfect, with no flaws. Now I'm able to get it to work, but only by using the method of hitting ESC and booting another way, and even then, there's no sound. When I let it boot up normally, it goes to "Starting up..." and stays there. Now to answer the big question of what the garbage text said, well I'm not really sure. I'm not good with using the Ubuntu Linux software, in face, I'm not really sure how to use computers all that well, which is why I naturally don't have a clue what anything said. I can post a picture later if you all want.

---

### Post by Leppie on 2010-02-04
well, if you can boot into your system normally, issue the following command in a terminal:
```
sudo grub-install --recheck /dev/sda
```
this should re-install grub to the mbr.
then issue the followign command to (re)generate the grub.cfg:
```
sudo update-grub
```

---

### Post by pojr on 2010-02-05
Thanks, but when you say boot normally, you mean without loading the [**menu I posted a picture of**](http://imgh.us/676A0033.jpg), or simply letting the computer turn on without me doing anything? Because when I let it turn on without me doing anything, it leads to a blank screen that says "Starting up."

Btw, the reason I have my messages in such detail is so that there are not as many questions. Just making sure. :)

---

### Post by Leppie on 2010-02-05
> **pojr said:**
> Thanks, but when you say boot normally, you mean without loading the [**menu I posted a picture of**]("http://imgh.us/676A0033.jpg"), or simply letting the computer turn on without me doing anything? Because when I let it turn on without me doing anything, it leads to a blank screen that says "Starting up." 
no, with booting normally i mean  booting into your ubuntu install without the need of a cd or such.

---

### Post by pojr on 2010-02-05
Okay, I'll try that code then. Thanks.

---

### Post by Leppie on 2010-02-05
ok, let us know how it goes.

---

### Post by pojr on 2010-02-06
Here's exactly what I did:

```
daniel@pojr:~$ sudo grub-install --recheck /dev/sda
[sudo] password for daniel: 
Probing devices to guess BIOS drives. This may take a long time.
Searching for GRUB installation directory ... found: /boot/grub
Installing GRUB to /dev/sda as (hd0)...
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)	/dev/fd0
(hd0)	/dev/sda
daniel@pojr:~$ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.31-16-generic
Found kernel: /boot/vmlinuz-2.6.31-14-generic
Found kernel: /boot/vmlinuz-2.6.28-16-generic
Found kernel: /boot/vmlinuz-2.6.27-15-generic
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

daniel@pojr:~$ 

```

Nothing appears different, including the non-functioning sound.

---

### Post by Leppie on 2010-02-06
could you [download and run meierfra's script]("http://sourceforge.net/projects/bootinfoscript/") and post the generated RESULTS.txt?

---

### Post by pojr on 2010-02-06
Thanks for that link. I dowloaded it, and the file **boot_info_script_051.sh** was added do my desktop. I clicked it, and the top of the link lead to instructions. The instructions said:

```
#!/bin/bash
#to use this script:
#
#     sudo bash boot_info_script050.sh
#or
#     su -
#     bash boot_info_script_050.sh
#
```

So I went to terminal, and typed in **sudo bash boot_info_script050.sh**. Terminal responded with [b]bash: boot_info_script050.sh: No such file or directory
[/b]

Then I noticed that the file that was on my desktop was named **boot_info_script051.sh**. That's funny, because the instructions referred to the file **boot_info_script050.sh** (with a 50 rather than 51). As a response, I renamed the file on my desktop to match the instructions. Then I typed the same thing in terminal. Unfortunately, the response Terminal gave was once again [b]bash: boot_info_script050.sh: No such file or directory
[/b]

I don't understand Ubuntu sometimes. Yeah, I agree that it's way more safe than Windows, and way better too, but I've noticed that Windows is way more straight forward than Ubuntu. Common sense doesn't seem to apply with Linux. Just saying. Who thought of making terminal required for every download?

---

### Post by Leppie on 2010-02-06
try the following command instead:
```
sudo bash ~/Desktop/boot_info_script*.sh
```

---

### Post by c0mput3r_n3rD on 2010-02-06
I would suggest downgrading to a more stable version such as 8.04 or 8.10  I have an IBM R40 that I tried loading up with Ubuntu 9.10 and it just flat out did not work; much like how yours is acting.  After downgrading to another version all was fine.  I believe 8.04 is Ubuntu's most stable release.  You also have way to many kernel versions up there, as you should only have 4 Ubuntu options.  Older computers just don't work that well with 9.10 in my experience.

---

### Post by Leppie on 2010-02-06
> **c0mput3r_n3rD said:**
> I believe 8.04 is Ubuntu's most stable release.
hardy heron (8.04) is the current lts. a lot of people (like me) use karmic without any issues though. stable depends more on your system. karmic should have more support for hardware.

> **c0mput3r_n3rD said:**
> You also have way to many kernel versions up there, as you should only have 4 Ubuntu options.
having "many options" in the boot menu doesn't affect a system at all. what if i have installed 5 different os's installed, all with several different kernel releases? i should not be able to run anything anymore?

 > **c0mput3r_n3rD said:**
> Older computers just don't work that well with 9.10 in my experience.
karmic should have more support for hardware. if there's issues, you most probably can find an answer here on the forum.

---

### Post by c0mput3r_n3rD on 2010-02-06
> **Leppie said:**
> hardy heron (8.04) is the current lts. a lot of people (like me) use karmic without any issues though. stable depends more on your system. karmic should have more support for hardware.


having "many options" in the boot menu doesn't affect a system at all. what if i have installed 5 different os's installed, all with several different kernel releases? i should not be able to run anything anymore?

 
karmic should have more support for hardware. if there's issues, you most probably can find an answer here on the forum.



He has 10 kernel options just for 9.10, I think that's too much.  And I've tried putting 9.10 on 4 computers that were more than 5 years old that just flat out did not work.

---

### Post by Leppie on 2010-02-06
> **c0mput3r_n3rD said:**
> He has 10 kernel options just for 9.10, I think that's too much.  And I've tried putting 9.10 on 4 computers that were more than 5 years old that just flat out did not work.
maybe you chose the wrong image to use? older equipment usually does better with the alternate cd install.

---

### Post by -kg- on 2010-02-06
> **c0mput3r_n3rD said:**
> He has 10 kernel options just for 9.10, I think that's too much.  And I've tried putting 9.10 on 4 computers that were more than 5 years old that just flat out did not work.

Has anyone looked closely at the kernel versions?  He's got some very old kernels listed there, the oldest of which is:

> Found kernel: /boot/vmlinuz-2.6.24-19-generic


I may be wrong, but I'm fairly sure that Karmic (or Jaunty, for that matter) didn't ship with *that* early of kernel.

No one has suggested the following yet (that I can find).  Try the command:

```
fdisk -l
```
(lowercase L)

and post the results.  I've seen nothing in previous posts that will show the partition setup on your disk(s).  With that old of a kernel, it might be possible that, if you had a previous installation, you installed it side-by-side with that installation.

---

### Post by Leppie on 2010-02-06
> **-kg- said:**
> Has anyone looked closely at the kernel versions?  He's got some very old kernels listed there, the oldest of which is:



I may be wrong, but I'm fairly sure that Karmic (or Jaunty, for that matter) didn't ship with *that* early of kernel.

No one has suggested the following yet (that I can find).  Try the command:

```
fdisk -l
```(lowercase L)

and post the results.  I've seen nothing in previous posts that will show the partition setup on your disk(s).  With that old of a kernel, it might be possible that, if you had a previous installation, you installed it side-by-side with that installation.
everything you are referring to will be handled by the boot info script. that's why i asked the OP to run it and post the output. waiting for the results...

and he actually does have a karmic kernel listed as well:
```

Found kernel: /boot/vmlinuz-2.6.31-16-generic
```

---

### Post by -kg- on 2010-02-06
> everything you are referring to will be handled by the boot info script.

So I see...now. :redface:

> and he actually does have a karmic kernel listed as well:

Yes, I know; probably one or two that came with Jaunty, as well.  It was just surprising to me that he had those old kernels still listed, especially the oldest one.

---

### Post by pojr on 2010-02-06
I was also thinking it could be because it's too advanced and that I should downgrade, but maybe I'll be able to keep the latest version by the end of this topic.

Anyway, that code did work, and here's the result:

```
============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf5229cee

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   190,081,079   190,081,017  83 Linux
/dev/sda2         190,081,080   195,366,464     5,285,385   5 Extended
/dev/sda5         190,081,143   195,366,464     5,285,322  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        839fe156-11ed-47ac-9085-4e42c851ba45   ext3                                     
/dev/sda5        4bd6472e-08d1-4778-85a0-9564c878078b   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext3       (rw,relatime,errors=remount-ro)


=========================== sda1/boot/grub/menu.lst: ===========================

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
default		0Finished. The results are in the file RESULTS.txt located in /home/daniel/Desktop


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
# kopt=root=UUID=839fe156-11ed-47ac-9085-4e42c851ba45 ro

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

title		Ubuntu 9.10, kernel 2.6.31-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=839fe156-11ed-47ac-9085-4e42c851ba45 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=839fe156-11ed-47ac-9085-4e42c851ba45 ro  single
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=839fe156-11ed-47ac-9085-4e42c851ba45 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=839fe156-11ed-47ac-9085-4e42c851ba45 ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.28-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=839fe156-11ed-47ac-9085-4e42c851ba45 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=839fe156-11ed-47ac-9085-4e42c851ba45 ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.10, kernel 2.6.27-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-15-generic root=UUID=839fe156-11ed-47ac-9085-4e42c851ba45 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-15-generic
quiet

title		Ubuntu 9.10, kernel 2.6.27-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-15-generic root=UUID=839fe156-11ed-47ac-9085-4e42c851ba45 ro  single
initrd		/boot/initrd.img-2.6.27-15-generic

title		Ubuntu 9.10, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=839fe156-11ed-47ac-9085-4e42c851ba45 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 9.10, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=839fe156-11ed-47ac-9085-4e42c851ba45 ro  single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 9.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=839fe156-11ed-47ac-9085-4e42c851ba45 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=4bd6472e-08d1-4778-85a0-9564c878078b none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

Or you can download it here:

---

### Post by Leppie on 2010-02-07
the output looks truncated...
did you let the script complete all?

---

### Post by pojr on 2010-02-07
Yeah, I let it finish. Here's what I did:

```
daniel@pojr:~$ sudo bash ~/Desktop/boot_info_script*.sh
[sudo] password for daniel: 
Identifying MBRs...

Computing Partition Table of /dev/sda...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda5 for information... 
Finished. The results are in the file RESULTS.txt located in /home/daniel/Desktop
daniel@pojr:~$ 

```

After trying again, I got the following. It may be exactly the same was the previous link I posted.

---

### Post by oldfred on 2010-02-07
I did a clean install on my 3 year old Toshiba and it works just fine. I use it more as a desktop when not at home so I am not testing all laptop functions.

Because you upgraded it left all the old 9.04 kernels but the grub script puts 9.10 in the description by default. they will not work with the new files. It would be best to remove all the old kernels and run update-grub to refresh grub.cfg.

In synaptic search for linux-image to choose to delete old ones, keep all 2.6.31.xx for now. Later you may be able to delete all but the two most current.

Sudo update-grub

---

### Post by pojr on 2010-02-07
I'm not really sure what kernels are, nor how to remove them.

```
daniel@pojr:~$ Sudo update-grub
No command 'Sudo' found, did you mean:
 Command 'udo' from package 'udo' (universe)
 Command 'sudo' from package 'sudo' (main)
 Command 'sudo' from package 'sudo-ldap' (universe)
Sudo: command not found
daniel@pojr:~$ 

```

---

### Post by oldfred on 2010-02-07
> **pojr said:**
> I'm not really sure what kernels are, nor how to remove them.

```
daniel@pojr:~$ Sudo update-grub
No command 'Sudo' found, did you mean:
 Command 'udo' from package 'udo' (universe)
 Command 'sudo' from package 'sudo' (main)
 Command 'sudo' from package 'sudo-ldap' (universe)
Sudo: command not found
daniel@pojr:~$ 

```

Sorry typo on my part as Linux knows capitals are different than lower case.

sudo update-grub

Run that after going into synaptic to remove old kernels.
from your boot info:
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=839fe156-11ed-47ac-9085-4e42c851ba45 ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

all the ones less than 2.6.31.xx are older like the 2.6.28.xx above.

---

### Post by pojr on 2010-02-07
I attempted to look for Synaptic, and found it under administration. I deleted all three Kernel files that were under the number, and than went to terminal to type in **sudo upgrade-grub** with a lower-case s, and than when it was finished, I shut it down and attempted to turn it on. [**Here is the result**](http://www.youtube.com/watch?v=YVFOycUirEw).

---

### Post by oldfred on 2010-02-07
It is booting, did your try recovery mode to see if that boots all the way?

---

### Post by pojr on 2010-02-07
I tried loading **Kernel 2.6.31-16 generic (recovery mode)**, after loading text, it prompted me to a blue screen with options to boot, delete file space, fix errors, etc. naturally, I decided to select fix errors, and it said the computer would take about 15 minutes to load on a DSL connection, which I use. Currently, my computer screen is completely black, but appears to be loading...

---

### Post by audiomick on 2010-02-07
Looks like it is working away. Give it a bit more time....
The time estimates are never exactly accurate, and it can happen that the estimate is for one lot of stuff, and you come back expecting it to be just finished only to see it start on the next lot.

---

### Post by pojr on 2010-02-07
The result is shown below. What do I do next? Do I shut down and try booting normally without the recovery mode, or do I boot with recovery mode? In fact, do I shut down at all, or do I type something in on the screen?

---

### Post by audiomick on 2010-02-07
It looks like it is finished what it is doing.
the command to re-start should be
```
sudo shutdown -r now
```try that, and go for a normal boot.

---

### Post by pojr on 2010-02-07
I booted normally, and it loaded "Starting up..." I have no idea now.

---

### Post by TriadHonor on 2010-02-07
Why don't try to reinstall all from the beginning, after a good backup of your data ?

Maybe it is better, a clean install in a clean partition, maybe with a try using Wubi first, to test all without damage.

If you can load into your BIOS check the load sequence and check if HD0 is the first ( if you have more then one HD ), then the CD0.


On that point I'll prefer a clean install with Wubi to try first.

---

### Post by pojr on 2010-02-07
How do I reinstall 9.10? I have no clue how to do that. I don't know what Wubi is either.

---

### Post by Jackzor on 2010-02-07
I say a clean install of 8.04/8.10 As everyone says it runs better on older machines.

---

### Post by Jackzor on 2010-02-07
> **pojr said:**
> How do I reinstall 9.10? I have no clue how to do that. I don't know what Wubi is either.

Download and burn the cd then put it your Disk drive and turn on your computer. It should boot right to it and let you get on your way.

---

### Post by pojr on 2010-02-07
Is there a way to do it right on my computer, or do I have to hop on my other computer, burn it onto a disk, and install using the disk onto my Toshiba laptop?

---

### Post by Jackzor on 2010-02-07
Download links:

8.04 [http://releases.ubuntu.com/hardy/](http://releases.ubuntu.com/hardy/)            [I say get this]

8.10 [http://releases.ubuntu.com/8.10/](http://releases.ubuntu.com/8.10/)

9.04 [http://releases.ubuntu.com/9.04/](http://releases.ubuntu.com/9.04/)

9.10 [http://releases.ubuntu.com/9.10/](http://releases.ubuntu.com/9.10/)

---

### Post by Jackzor on 2010-02-07
> **pojr said:**
> Is there a way to do it right on my computer, or do I have to hop on my other computer, burn it onto a disk, and install using the disk onto my Toshiba laptop?

It would be best to get on another computer and download and burn it. Just besure you burn it as an image.

Depending on the Operating system you have on the other computer you may need to download something like [Alcohol 120% or Magic ISO (windows)]

---

### Post by audiomick on 2010-02-07
Bear in mind that a re-install will wipe your data, unless you have /home on a separate partition and re-mount it. If you don't know what that means, you probably don't have /home separate.

You can save stuff out of the install by booting into the live CD, i.e. the CD that you would install from. Choose that option "try without changing",; it will start Ubuntu in a "live environment", from where you can copy anything you want to keep to an external drive.

After this is finished, click on the "install Ubuntu" icon on the desktop, and the installer should start. If it doesn't, re-boot and choose "install" from the menu.

---

### Post by Leppie on 2010-02-07
> **pojr said:**
> Is there a way to do it right on my computer, or do I have to hop on my other computer, burn it onto a disk, and install using the disk onto my Toshiba laptop?
check the md5sum after downloading and after burning onto cd at a low speed (less than 10x). this is more important than changing pc or anything like that.
it will also tell you if your cd/dvd drive has issues.

---

### Post by TriadHonor on 2010-02-08
Yeah, maybe older one works better on your pc.

My suggestion is to boot all from a Live CD ( Linux or Windows, just to save your data, so if you like Linux try one of the live cd they linked, or for Windows use Windows PE, from BartPE ---> [http://www.nu2.nu/pebuilder/](http://www.nu2.nu/pebuilder/) ).

After the backup of your data yo ucan prceed 2 ways:

1- Using Wubi
2- Installing Linux "for real"

Wubi is a program for Windows who create a file of a dimension You choose and installing Linux there, then it provide a dual boot like a normal installation to choose what system run, like a normal dual boot, but you can always delete all from Windows like a normal installed program.

Link: [http://wubi-installer.org/](http://wubi-installer.org/)

Keep in mind that it download Karmic, if you want to install another distribution you must put the ISO in the same folder of Wubi.

I think this is the better way to try if your pc support Linux, and which distribution, because if something don't work you simply log in Windows and delete all, then you can try anotehr time.

---

