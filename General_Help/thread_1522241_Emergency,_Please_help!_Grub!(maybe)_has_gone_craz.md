---
title: "Emergency, Please help! Grub!?(maybe) has gone crazy!"
date: 2010-07-01
forum: General Help
---

### Post by EdwardJS on 2010-07-01
Hello, 

I have finally convinced my wife to migrate to Ubuntu, on this her first night of having it and after HOURS of installing, updating and upgrading we had a power outage. The entire grid in our community went down. Well, after the power returned I tried starting her computer back up and this is what happens:

Bios loads
Grub starts
A ton of scrolling words I can't read flash by on the screen
The monitor says "No Signal"

The computer remains on, but just sits there. I have tested the video card and it works. _I do not get dropped to a cli_. Please help me, I am at a total loss. Everything I have found, in the way of a solution, all require a command line, which I am not getting.

Sorry if this seems rushed, we are both quite frustrated as she has reports that she's supposed to be working on. I would be very grateful for any assistance. 

Thank you for your time.
Edward

---

### Post by mr clark25 on 2010-07-01
just to test if you have a hardware fault, see if you can boot from a live cd/usb drive.

if you can still boot from a cd or usb drive, then your computer should be fine.

if it doesnt boot from the cd, then something inside your computer is bad.



it sounds like your computer is fine.


usually grub doesn't have to much output when it has errors. it is probably the ubuntu install that got damaged.

---

### Post by EdwardJS on 2010-07-02
Thank you for replying. 

I can indeed boot from a live disk. I can access all the files on the hard drive from the livecd and nothing appears to be broken, damaged or missing.

Would you mind clarifying what you mean by "it is probably the ubuntu install that got damaged"?

Is there a repair utility or test I can run to help resolve this issue? Your comment sounds ominously like a reinstall is required.

Once again, thank you for willing to help me tonight, she really needs to be able to finish her work as soon as possible. 

Edward

---

### Post by oldfred on 2010-07-02
With Ubuntu you can change some settings and only when you reboot do they take effect as you were still using system with old settings. Power failure force reboot.

Did you change any video settings that then make it not boot.

What video card do you have?

From grub menu can you choose rescue mode? And have you tried some of the things it suggests.(if you have 10.04).

---

### Post by EdwardJS on 2010-07-02
> **oldfred said:**
> With Ubuntu you can change some settings and only when you reboot do they take effect as you were still using system with old settings. Power failure force reboot.

Did you change any video settings that then make it not boot.

What video card do you have?

From grub menu can you choose rescue mode? And have you tried some of the things it suggests.(if you have 10.04).


The system was fully upgraded, and up-to-date. No old settings were in use when we lost power as there were no old settings. This was a clean, fresh install with the only changes made besides the updates being her files placed on the hard drive. 

The video card was working fine before the power outage (had not changed any drivers et cetera) and is still working, it is only after the screen flashes a bunch of words too fast for any human eye to read, does the monitor go into standby with "No signal".

Unfortunately, I cannot enter the grub menu. this however is a symptom of the USB keyboard on her computer I believe, that for some reason does not start up in time (always has been this way regardless of OS).

I would again reiterate my question from earlier, is there a tool or utility that I can run for the livecd to help me resolve issue? I should note, the livecd used is 8.10 (intrepid ibex). Her computer was updated from there to 10.04


Thank you again for your replies, I am truly grateful. If looks could kill, my wife... Well, let's just say I'd be dead.

Edward

---

### Post by EdwardJS on 2010-07-02
bump

I know it hasn't been long but this really is urgent. I need to reslove this issue as soon as possible. Please, is there anybody that has any ideas?

---

### Post by artemyv on 2010-07-02
> **EdwardJS said:**
> 
I would again reiterate my question from earlier, is there a tool or utility that I can run for the livecd to help me resolve issue? I should note, the livecd used is 8.10 (intrepid ibex). Her computer was updated from there to 10.04


What about trying to boot to 10.04 live cd? Maybe lucid has some problems with the hardware?

---

### Post by Segofam on 2010-07-02
Hey, I tried to load Lucid Lynx on a Compaq Presario that was or is about five years old. I ask folks here and got a good response, but alas no luck. I then phone a guy in Brisbane who informed me that Lucid Lynx did not have the drivers required to run on the Compaq.
All that happened was the Ubuntu with a purple background and some little while dots going from left to right would come up, after that it would just flash some bad video graphics and freeze/stop.
I then loaded the previous version and it worked fine.
Sorry to tell you that it just maybe the same scenario, but I hope not.
Kind regards,
Scott

---

### Post by oldfred on 2010-07-02
If it is a boot issue and not a video issue this may tell something.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by RJARRRPCGP on 2010-07-02
> **EdwardJS said:**
> Hello, 

I have finally convinced my wife to migrate to Ubuntu, on this her first night of having it and after HOURS of installing, updating and upgrading we had a power outage. The entire grid in our community went down. Well, after the power returned I tried starting her computer back up and this is what happens:

Bios loads
Grub starts
A ton of scrolling words I can't read flash by on the screen
The monitor says "No Signal"

The computer remains on, but just sits there. I have tested the video card and it works. _I do not get dropped to a cli_. Please help me, I am at a total loss. Everything I have found, in the way of a solution, all require a command line, which I am not getting.

Sorry if this seems rushed, we are both quite frustrated as she has reports that she's supposed to be working on. I would be very grateful for any assistance. 

Thank you for your time.
Edward

Sounds like your HDD got corrupted. You should just wipe the HDD and start over. Sorry. :(

Looks like you should DBAN it and start over. Or use MHDD and wipe sectors 0 to 222222 and start over.

---

### Post by EdwardJS on 2010-07-02
Thanks for the responses so far guys, unfortunately I was not able to resolve this issue as quickly as I needed to and therefore no longer have the urgency I did last night.

> **Segofam said:**
> 
All that happened was the Ubuntu with a purple background and some little while dots going from left to right would come up, after that it would just flash some bad video graphics and freeze/stop.
Scott

Thank you for your input, however I am faced with a different set of symptoms.

> **RJARRRPCGP said:**
> Sounds like your HDD got corrupted. You should just wipe the HDD and start over. Sorry. :(

Looks like you should DBAN it and start over. Or use MHDD and wipe sectors 0 to 222222 and start over.

This is what I was most afraid of but had a feeling would be required. Thank you for your reply.

> **oldfred said:**
> If it is a boot issue and not a video issue this may tell something.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

Before I attempt the previous suggestion of wiping and starting over as I would very much like to avoid it, as I would learn nothing about the problem or the actual solution in the process. Therefore I will take your advice and try this first. Thank you for the link, I will keep you updated.

---

### Post by Rubi1200 on 2010-07-02
> **EdwardJS said:**
> Before I attempt the previous suggestion of wiping and starting over as I would very much like to avoid it, as I would learn nothing about the problem or the actual solution in the process. Therefore I will take your advice and try this first. Thank you for the link, I will keep you updated.

Please follow oldfred's advice; he knows what he is talking about!

---

### Post by EdwardJS on 2010-07-02
```
   Boot Info Script 0.55    dated February 15th, 2010                   

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 10.04 LTS
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

Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders, total 39102336 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x02190219

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    37,383,254    37,383,192  83 Linux
/dev/sda2          37,383,255    39,102,209     1,718,955   5 Extended
/dev/sda5          37,383,318    39,102,209     1,718,892  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders, total 39102336 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0f800000

Partition  Boot         Start           End          Size  Id System



blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                        

/dev/loop0                                              squashfs                                
/dev/ramzswap0                                          swap                                    
/dev/sda1        2462b099-2d8c-47cf-81e1-9e0e65335e8f   ext3                                    
/dev/sda5        b62b64c6-081a-41ce-ba84-ed902ccea5ef   swap                                    

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/scd0        /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

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
# kopt=root=UUID=2462b099-2d8c-47cf-81e1-9e0e65335e8f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=2462b099-2d8c-47cf-81e1-9e0e65335e8f

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

title        Ubuntu 10.04 LTS, kernel 2.6.32-23-generic
uuid        2462b099-2d8c-47cf-81e1-9e0e65335e8f
kernel        /boot/vmlinuz-2.6.32-23-generic root=UUID=2462b099-2d8c-47cf-81e1-9e0e65335e8f ro quiet splash
initrd        /boot/initrd.img-2.6.32-23-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.32-23-generic (recovery mode)
uuid        2462b099-2d8c-47cf-81e1-9e0e65335e8f
kernel        /boot/vmlinuz-2.6.32-23-generic root=UUID=2462b099-2d8c-47cf-81e1-9e0e65335e8f ro  single
initrd        /boot/initrd.img-2.6.32-23-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-22-generic
uuid        2462b099-2d8c-47cf-81e1-9e0e65335e8f
kernel        /boot/vmlinuz-2.6.31-22-generic root=UUID=2462b099-2d8c-47cf-81e1-9e0e65335e8f ro quiet splash
initrd        /boot/initrd.img-2.6.31-22-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.31-22-generic (recovery mode)
uuid        2462b099-2d8c-47cf-81e1-9e0e65335e8f
kernel        /boot/vmlinuz-2.6.31-22-generic root=UUID=2462b099-2d8c-47cf-81e1-9e0e65335e8f ro  single
initrd        /boot/initrd.img-2.6.31-22-generic

title        Ubuntu 10.04 LTS, kernel 2.6.28-19-generic
uuid        2462b099-2d8c-47cf-81e1-9e0e65335e8f
kernel        /boot/vmlinuz-2.6.28-19-generic root=UUID=2462b099-2d8c-47cf-81e1-9e0e65335e8f ro quiet splash
initrd        /boot/initrd.img-2.6.28-19-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.28-19-generic (recovery mode)
uuid        2462b099-2d8c-47cf-81e1-9e0e65335e8f
kernel        /boot/vmlinuz-2.6.28-19-generic root=UUID=2462b099-2d8c-47cf-81e1-9e0e65335e8f ro  single
initrd        /boot/initrd.img-2.6.28-19-generic

title        Ubuntu 10.04 LTS, kernel 2.6.27-17-generic
uuid        2462b099-2d8c-47cf-81e1-9e0e65335e8f
kernel        /boot/vmlinuz-2.6.27-17-generic root=UUID=2462b099-2d8c-47cf-81e1-9e0e65335e8f ro quiet splash
initrd        /boot/initrd.img-2.6.27-17-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.27-17-generic (recovery mode)
uuid        2462b099-2d8c-47cf-81e1-9e0e65335e8f
kernel        /boot/vmlinuz-2.6.27-17-generic root=UUID=2462b099-2d8c-47cf-81e1-9e0e65335e8f ro  single
initrd        /boot/initrd.img-2.6.27-17-generic

title        Ubuntu 10.04 LTS, memtest86+
uuid        2462b099-2d8c-47cf-81e1-9e0e65335e8f
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=2462b099-2d8c-47cf-81e1-9e0e65335e8f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=b62b64c6-081a-41ce-ba84-ed902ccea5ef none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   3.2GB: boot/grub/menu.lst
   3.1GB: boot/grub/stage2
   3.2GB: boot/initrd.img-2.6.27-17-generic
   3.1GB: boot/initrd.img-2.6.28-19-generic
   3.2GB: boot/initrd.img-2.6.31-22-generic
   3.4GB: boot/initrd.img-2.6.32-23-generic
   3.1GB: boot/vmlinuz-2.6.27-17-generic
   3.1GB: boot/vmlinuz-2.6.28-19-generic
   3.1GB: boot/vmlinuz-2.6.31-22-generic
   3.2GB: boot/vmlinuz-2.6.32-23-generic
   3.4GB: initrd.img
   3.2GB: initrd.img.old
   3.2GB: vmlinuz
   3.1GB: vmlinuz.old
```

---

### Post by oldfred on 2010-07-02
I do not see anything in your results.txt that looks out of place. It must be an upgrade to 10.04 as you still have grub legacy.

Since you only have Ubuntu you should not see the grub menu. Hold escape key (escape old grub, shift in grub2) from the BIOS boot until the menu appears. Try booting the recovery mode and see if you get to a command line. That would then indicate it is a video issue or when ever the boot stops you may be able to see what commands it processed last. We then could check logs if necessary.

Oops, sdb is not showing any partitions. Does not look like it should prevent booting. Is it not formated or does it have problems?

---

### Post by WorMzy on 2010-07-02
I second booting into recovery mode. If the recovery options don't help, then try dropping to a root shell and renaming xorg.conf:
```
cd /etc/X11 && mv xorg.conf xorg.conf.old
``` unlike previous versions of Ubuntu, Lucid doesn't need xorg.conf, and will happily run without it.

---

### Post by EdwardJS on 2010-07-02
> **oldfred said:**
> I do not see anything in your results.txt that looks out of place. It must be an upgrade to 10.04 as you still have grub legacy.

Since you only have Ubuntu you should not see the grub menu. Hold escape key (escape old grub, shift in grub2) from the BIOS boot until the menu appears. Try booting the recovery mode and see if you get to a command line. That would then indicate it is a video issue or when ever the boot stops you may be able to see what commands it processed last. We then could check logs if necessary.

Oops, sdb is not showing any partitions. Does not look like it should prevent booting. Is it not formated or does it have problems?

Thanks for the reply.
I will try holding the key down, although as stated earlier I am not sure it will work as the keyboard doesn't turn on in time. The video card works with the livecd as we speak, and was working all day yesterday with 10.04 with no issues until the power outage so I am not sure that's the issue. sdb is unformatted for the time being, a situation I was to remedy yesterday before this happened.

I will give it a try and keep you updated. Thanks again.
Edward

---

### Post by WorMzy on 2010-07-02
Oh, and if all else fails, I recommend making a backup of all the documents and other important files, then formatting the partition and installing a fresh copy of Lucid.

Formatting should be a last resort though.

---

### Post by oldfred on 2010-07-02
If the keyboard does not work in grub check your BIOS settings.

A year or so ago I installed a new motherboard. But USB keyboard did not work in grub but was ok in windows & ubuntu. I did find keyboard worked with ps/2 adapter, but that was a hassle. It of course was a BIOS setting that grub was reading but both windows and Ubuntu were ignoring.

---

