---
title: "HELP ASAP - Ubuntu Installation changed bootloader and drive letters"
date: 2011-04-09
forum: General Help
---

### Post by EarthBoundX5 on 2011-04-09
Ok, this has totally pissed me off; and I am here to seek help before going further as this is my desktop (aka, my baby, lol, but seriously...).  I decided I wanted to finally put ubuntu as an option of my desktop pc, but I refused to alter the primary drive in any way (I have had alot of bad experiences dual/triple booting with my laptop and CANNOT have ANY similar problems happen to my desktop), so I installed an extra 160GB drive to use for other OSs.  Anyways, I will list off what I have done to make things as clear as possible....

========================================================

1. Booted into Ubuntu 10.10 Live to format the new drive before installing.
    *Created 3 Primary and the Extended.
    *40GB Ubuntu, 5.9GB Swap, 60GB FAT32(to eventually be reformatted for OSX86)
2. Installed Ubuntu, selecting the proper partition as "/"
3. Proceeded to reboot and selected said drive via BIOS boot options, would not boot.
    *Restarted to boot normally fearing what may have happened, and of course there I see it, GRUB!!
4. I was able to boot Windows fine via GRUB, but it was unacceptable, I restarted and booted to a Windows 7 recovery disk to see if claiming my partition for windows is D:.

========================================================

I would like some advice/help as to what I need to do to accomplish the following....
1. Restore the default boot manager to Windows 7 as it was before along with main partition being C: rather than D:
2. Reinstall Ubuntu (yes, I know I dont HAVE to) so that GRUB is ONLY ON THE OTHER HDD, not my primary one.

Again, this is my baby, I can't have ANYTHING go wrong so I do not trust myself to go any further without input from another.  I would also like someone to answer me this; [CapsLock off to be nice, but know I wanted to use it, haha] Why in the hell does the Ubuntu installation even touch any drive other than the one selected for installation?

I can provide any additional info needed, if I left out anything or this all seems like a mess of words, just realise I am in a state of fear and panic (even though I am well aware this problem is more than easily reversible).

---

### Post by Hedgehog1 on 2011-04-09
To get your PC to boot directly into Windows again:

To make a Windows 7 / Vista emergency repair disk (in case you don't already have one made):
[IMG]http://img641.imageshack.us/img641/9550/small50createrepairdisk.png[/IMG]

If you are unable to make a recovery disk, you can download the ISO for   [VISTA]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") or [WINDOWS7]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

Boot from the windows 7 / Vista  emergency repair disk, do the following:
[IMG]http://img10.imageshack.us/img10/5826/small51runningrecoveryd.png[/IMG]
[IMG]http://img856.imageshack.us/img856/3690/small52selectingwindows.png[/IMG]
[IMG]http://img826.imageshack.us/img826/3484/small53commandprompt.png[/IMG]
[IMG]http://img215.imageshack.us/img215/9547/small54bootrec.png[/IMG]


***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-04-09
To have Ubuntu only on the 2nd drive:

The image below is setting up the 3rd drive (/dev/sdc), but I think you want to do this for /dev/sdb (2nd drive), so please mentally replace the **/dev/sdc**'s for **/dev/sdb**'s:

[IMG]http://img684.imageshack.us/img684/7977/mbrpariondemo16.png[/IMG]


If you install the bootloader on **/dev/sdb**, you will then have to boot the isolated Ubuntu install using the BIOS 'select boot device' function (which is what you want)

**The Hedge**

:KS

p.s. The install above had separate '/' (root) and '/home' partitions, your install may be different.

---

### Post by Bucky Ball on 2011-04-09
Nice one Hedge. This should help. 

Earthbound; if you can't afford to have anything go wrong why install a rolling release like 10.10? I would advise you go for the current long term support release 10.04 LTS as it is more stable and five years support.

I have four computers, all except this one (my kinda stable plaything) ALWAYS run on an LTS as my wife and I are at uni and can't afford to have downtime, especially when an essay is due tomorrow ... ;)

Downtime for me is the two and a half month Christmas break ... then I can tweak my brain off!!! lol

Incidentally, sounds like you have grub installed to the wrong partition ... check Hedge's instructions ...

---

### Post by EarthBoundX5 on 2011-04-09
Side Note: I am officially atm changing my DNS servers from my default ISP (Qwest) ones, my god are they unreliable.

Anyways, here is what I was gonna say like 5 mins ago...

Thanks alot Hedge, that is actually the exact point I was sitting at, just waiting for confirmation before I clicked enter.

That  being said, part 2, do you know how to install 10.10 with grub  remaining on the drive to which ubuntu is installed?  I know with 10.04  there was an option, but I didn't see anything during 10.10.  <-I see you responded, but like I said, I don't recall seeing that screencap in 10.10, but I could be blind

Also,  I am fully aware that grub may never have been installed to my primary  drive, I just assume so as when I selected the drive ubuntu was on, it  would not boot at all.  Thanks again, both of you, for the quick replies.

EDIT: >Bucky Ball: Because I did not foresee any issues installing to a completely separate drive, so I didn't care about using a more stable version, as I didn't anticipate problems.  That and I have already installed 10.10 on about 3 other computers and upgraded one from 10.04 to it.

EDIT 2: You know what, nvm, no more wasting your guy's time.  I'm just gonna try again, if I see no option, I will go with 10.04 and upgrade to 10.10 if I feel the urge.

---

### Post by Hedgehog1 on 2011-04-09
> **EarthBoundX5 said:**
> Why in the hell does the Ubuntu installation even touch any drive other than the one selected for installation?

Under normal situations, most users are expecting a single menu of all OS's.  To make this happen, we need a single 'starting' point, and that point on your machine is the boot block of /dev/sda.

Your desire to keep the disks completely isolated requires a BIOS knowledge not all users have (or may have and don't want to deal with).

As a side note:  The install of the grub bootloader in /dev/sdb will create a menu that also includes the option to start windows on your /dev/sda drive.  If you do not want the windows install showing in the grub menu from /dev/sdb, please do these two steps:

```
sudo rm /etc/grub.d/30_os-prober
```

```
sudo update-grub
```


***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-04-09
> **Bucky Ball said:**
> Earthbound; if you can't afford to have anything go wrong why install a rolling release like 10.10? I would advise you go for the current long term support release 10.04 LTS as it is more stable and five years support.

+1 on using the very nice 10.04.02 LTS. **Bucky Ball** is quite right that you will have the most stable install that way.


***The Hedge***

:KS

p.s. Thanks for noticing, Bucky Ball...

**EDIT:** You already run 10.10 on other machines - never mind - you know what you will be getting, then!

---

### Post by EarthBoundX5 on 2011-04-09
Again, thanks for the continued response.  You know, this actually may be a good time to address a similar issue, and by similar I mean boot loader related.  I will spare the details, and just state the current status of my laptop....

Grub Loader, shows Windows 7 as an option, cant boot to it via Grub, currently only way to access Windows is via Bootmgr on a disc.  

Don't even begin to ask me what happend, lol, but if you know away to completely repair the Windows 7 boot manager while preserving Grub, please tell me, as I have tried everything I can think of.

If my terrible explanation is too horrible, forget it, as I can live atm using a boot cd, as I use ubuntu mostly on my laptop anyways, but it sure is an annoyance.

---

### Post by Hedgehog1 on 2011-04-09
> **EarthBoundX5 said:**
> 
1. Booted into Ubuntu 10.10 Live to format the new drive before installing.
    *Created 3 Primary and the Extended.
    *40GB Ubuntu, 5.9GB Swap, **_60GB FAT32(to eventually be reformatted for OSX86)_**


EarthBoundX5,

To maintain the 'one OS per hard drive' without any dual booting, you will need to install OSX86 on its own 3rd hard drive and then select it using the BIOS boot select feature.


***The Hedge***

:KS

---

### Post by EarthBoundX5 on 2011-04-09
> **Hedgehog1 said:**
> To maintain the 'one OS per hard drive' without any dual booting, you will need to install OSX86 on its own 3rd hard drive and then select it using the BIOS boot select feature.

The one OS per drive thing is more of a 1 Drive for Windows, 1 Drive for Temp/Downloading, 1 Drive (the new one) for multiple OSs.  I just worry about my Windows drive, as its 750 GB, and has way too much time put into it to risk anything going wrong with it)

EDIT: NOTE: I applaud your thorough attitude, many people just stop after solving the problem at hand.  Thanks alot for taking the time to read and verify everything I said.

---

### Post by Hedgehog1 on 2011-04-09
> **EarthBoundX5 said:**
> The one OS per drive thing is more of a 1 Drive for Windows, 1 Drive for Temp/Downloading, 1 Drive (the new one) for multiple OSs.  I just worry about my Windows drive, as its 750 GB, and has way too much time put into it to risk anything going wrong with it)


OK, I understand now.  Thanks for explaining.

Also THANKS for marking the thread SOLVED, so few people do that!


**The Hedge**

:KS

---

### Post by EarthBoundX5 on 2011-04-09
> **Hedgehog1 said:**
> Also THANKS for marking the thread SOLVED, so few people do that!

I am not sure if I did exactly :( lol, I thought I did with an advanced edit of the OP post, but its still showing up differently in the forums...

EDIT: Oh, and did you see my other question?  Or was did you just ignore it like I suggested if I had worded it too poorly?

---

### Post by Hedgehog1 on 2011-04-09
> **EarthBoundX5 said:**
> I am not sure if I did exactly :( lol, I thought I did with an advanced edit of the OP post, but its still showing up differently in the forums...

EDIT: Oh, and did you see my other question?  Or was did you just ignore it like I suggested if I had worded it too poorly?

Please re-ask the missed question, I have lost track of it (My little Hedgie brain is overloaded) :D

***The Hedge***

:KS

p.s. You can set the thread to solved using the thread tools in the upper right side of the thread.

---

### Post by EarthBoundX5 on 2011-04-09
> **Hedgehog1 said:**
> Please re-ask the missed question, I have lost track of it (My little Hedgie brain is overloaded) :D

> **EarthBoundX5 said:**
> Again, thanks for the continued response.   You know, this actually may be a good time to address a similar issue,  and by similar I mean boot loader related.  I will spare the details,  and just state the current status of my laptop....

Grub Loader, shows Windows 7 as an option, cant boot to it via Grub,  currently only way to access Windows is via Bootmgr on a disc.  

Don't even begin to ask me what happend, lol, but if you know away to  completely repair the Windows 7 boot manager while preserving Grub,  please tell me, as I have tried everything I can think of.

If my terrible explanation is too horrible, forget it, as I can live atm  using a boot cd, as I use ubuntu mostly on my laptop anyways, but it  sure is an annoyance.

Oh, and I guess I am blind, as I definitely see the boot loader option now.  Wow I feel stupid for not being more careful.

EDIT: My blindness also explains why when I went to thread tools originally to mark as solved, I did not see the obvious option, lol.

EDIT 2: DAMMIT!!  Ubuntu installed fine (changed boot loader location), and now I am having wireless problems?!?!  Why can I have no joy today??  I use static routing, because I refuse to use DHCP (you can call me stupid if you like, but I grew up without DHCP and always did well).  I'm gonna try somethings, but I am confused as hell.  I have the MAC address and IP saved on my router, but neither that IP nor any other IP will alow it to connect...

---

### Post by Hedgehog1 on 2011-04-09
> Grub Loader, shows Windows 7 as an option, cant boot to it via Grub, currently only way to access Windows is via Bootmgr on a disc. 

Don't even begin to ask me what happend, lol, but if you know away to completely repair the Windows 7 boot manager while preserving Grub, please tell me, as I have tried everything I can think of.

If my terrible explanation is too horrible, forget it, as I can live atm using a boot cd, as I use ubuntu mostly on my laptop anyways, but it sure is an annoyance.

There is a fair chance we can correct the laptop situation, too.  

If you would, please boot from Ubuntu on your laptop and do this:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the two 'CODE' tags.

***The Hedge***

:KS

p.s. Blindness and panic cause the same symptoms... :D

---

### Post by EarthBoundX5 on 2011-04-09
> **Hedgehog1 said:**
> There is a fair chance we can correct the laptop situation, too.  

If you would, please boot from Ubuntu on your laptop and do this:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 296170304 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   238,237,695   238,235,648   7 HPFS/NTFS
/dev/sda2         238,237,696   245,473,279     7,235,584   7 HPFS/NTFS
/dev/sda4         245,473,280   312,580,079    67,106,800   5 Extended
/dev/sda5         245,475,328   307,859,455    62,384,128  83 Linux
/dev/sda6         307,861,504   312,580,079     4,718,576  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1                                               ntfs       SYSTEM                        
/dev/sda2        40388943388938C4                       ntfs       RAMDRIVE                      
/dev/sda4: PTTYPE="dos" 
/dev/sda5        78c324f2-e4ec-4a1e-aee2-9dde3a496301   ext4                                     
/dev/sda6        ba6b9145-5389-4e2d-836c-b05e2c6d0216   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=600)
/dev/sr0         /media/HBCD              iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 78c324f2-e4ec-4a1e-aee2-9dde3a496301
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 78c324f2-e4ec-4a1e-aee2-9dde3a496301
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 78c324f2-e4ec-4a1e-aee2-9dde3a496301
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=78c324f2-e4ec-4a1e-aee2-9dde3a496301 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 78c324f2-e4ec-4a1e-aee2-9dde3a496301
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=78c324f2-e4ec-4a1e-aee2-9dde3a496301 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 78c324f2-e4ec-4a1e-aee2-9dde3a496301
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 78c324f2-e4ec-4a1e-aee2-9dde3a496301
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 0000000000000000
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda5       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=ba6b9145-5389-4e2d-836c-b05e2c6d0216 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 132.3GB: boot/grub/core.img
 133.3GB: boot/grub/grub.cfg
 140.2GB: boot/initrd.img-2.6.35-28-generic
 129.1GB: boot/vmlinuz-2.6.35-28-generic
 140.2GB: initrd.img
 129.1GB: vmlinuz
```

EDIT: Well that's great...I have no idea why I can't get my wireless working on my desktop ubuntu install...I even tried enabling DHCP to see if that was the problem...

---

### Post by Hedgehog1 on 2011-04-09
OK - this one is rather interesting!

Your Windows boot partition has no UUID, and that is confusing the 'update-grub' process:

```
Device           UUID                                   TYPE       LABEL                         

**[COLOR="red"]/dev/sda1[/COLOR]**                                               ntfs       SYSTEM                        
/dev/sda2        40388943388938C4                       ntfs       RAMDRIVE
```


```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set **[COLOR="Red"]0000000000000000[/COLOR]**
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###
```

Notice that without a UUID assigned to the Windows boot partition, grub just uses an all zero string.  There is no partition called '**[COLOR="Red"]0000000000000000[/COLOR]**, so that menu option fails.

We need to assign a UUID to /dev/sda1, and then run 
```
sudo update-grub
``` from the Ubuntu install on the hard drive.

I don't recall the command to add a UUID to a partition that doesn't have one; but I know it can be done.

A little research is needed.


***The Hedge***

:KS

---

### Post by EarthBoundX5 on 2011-04-09
> **Hedgehog1 said:**
> A little research is needed.

I came across [this]("http://www.linux-archive.org/debian-user/416755-adding-uuid-partition.html") thinking: hey that sounds like they will have an answer for added a UUID...but no, the user seems to just have been confused or something, as the thread ends with 'hey, there is the UUID', lmao

EDIT: So is not having a UUID supposed to make a partition unmountable?  Because I can mount it fine in ubuntu and boot to it fine with a bootmgr disc....lol

---

### Post by Hedgehog1 on 2011-04-09
It is not unmountable.  Grub just counts on a UUID or (in NTFS) a Volume Serial Number.

I found the command for updating the Volume Serial Number on an NTFS partition. The structure works like this:

```
sudo dd if=/dev/urandom of=/dev/**[ntfspartition]** bs=8 count=1 seek=9
```

For your laptop, please do these two commands:

```
sudo dd if=/dev/urandom of=/dev/**sda1** bs=8 count=1 seek=9
```

```
sudo update-grub
```

You should be able to boot into Windows from grub after that.


***The Hedge***

:KS

---

### Post by EarthBoundX5 on 2011-04-09
> **Hedgehog1 said:**
> You should be able to boot into Windows from grub after that.

If by Windows you mean booting the characters "+ã+ã", then success....lol, hope the scary dd command didn't just hurt my windows partition.

---

### Post by Hedgehog1 on 2011-04-09
> **EarthBoundX5 said:**
> If by Windows you mean booting the characters "+ã+ã", then success....lol, hope the scary dd command didn't just hurt my windows partition.

Sorry, I don't understand your post.  Are you able to boot into Windows from grub on the laptop?

Where is the "+ã+ã" displaying?


***The Hedge***

:KS

---

### Post by EarthBoundX5 on 2011-04-09
> **Hedgehog1 said:**
> Sorry, I don't understand your post.  Are you able to boot into Windows from grub on the laptop?

Where is the "+ã+ã" displaying?

I select Windows from Grub, it displays those symbols and then nothing...

EDIT: I'm gonna go take a nap/sleep.  I got tired of dealing with my  wireless problem with ubuntu on my desktop, and quit back to windows and  started doing a chkdsk because ubuntu's smart data claimed there was a  reallocated sector.  If you have any further ideas, please leave em here  and I'll respond when I wake up.

---

### Post by Hedgehog1 on 2011-04-09
> **EarthBoundX5 said:**
> I select Windows from Grub, it displays those symbols and then nothing

OK, so it is NOT working.  Please repeat these steps on the laptop: Boot from Ubuntu on and do this:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the two 'CODE' tags.


***The Hedge***

:KS

p.s. Oddly enough, I too am about to take a nap....

---

### Post by EarthBoundX5 on 2011-04-09
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 296170304 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   238,237,695   238,235,648   7 HPFS/NTFS
/dev/sda2         238,237,696   245,473,279     7,235,584   7 HPFS/NTFS
/dev/sda4         245,473,280   312,580,079    67,106,800   5 Extended
/dev/sda5         245,475,328   307,859,455    62,384,128  83 Linux
/dev/sda6         307,861,504   312,580,079     4,718,576  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        274A902DE056554D                       ntfs       SYSTEM                        
/dev/sda2        40388943388938C4                       ntfs       RAMDRIVE                      
/dev/sda4: PTTYPE="dos" 
/dev/sda5        78c324f2-e4ec-4a1e-aee2-9dde3a496301   ext4                                     
/dev/sda6        ba6b9145-5389-4e2d-836c-b05e2c6d0216   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=600)


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 78c324f2-e4ec-4a1e-aee2-9dde3a496301
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 78c324f2-e4ec-4a1e-aee2-9dde3a496301
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 78c324f2-e4ec-4a1e-aee2-9dde3a496301
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=78c324f2-e4ec-4a1e-aee2-9dde3a496301 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 78c324f2-e4ec-4a1e-aee2-9dde3a496301
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=78c324f2-e4ec-4a1e-aee2-9dde3a496301 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 78c324f2-e4ec-4a1e-aee2-9dde3a496301
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 78c324f2-e4ec-4a1e-aee2-9dde3a496301
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 274a902de056554d
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda5       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=ba6b9145-5389-4e2d-836c-b05e2c6d0216 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 132.3GB: boot/grub/core.img
 138.8GB: boot/grub/grub.cfg
 140.2GB: boot/initrd.img-2.6.35-28-generic
 129.1GB: boot/vmlinuz-2.6.35-28-generic
 140.2GB: initrd.img
 129.1GB: vmlinuz
```...and now I slumber[edit]...no longer

---

### Post by Hedgehog1 on 2011-04-10
I think I am understand why the dual boot on this laptop has been a nightmare.

The windows portion of the install is, well, ***ODD***.

Both Vista and Windows 7 normally install this way (I just did this 3 hours ago on laptop that needed a new hard drive)

Partition 1 - 100 Megs, Windows Boot Partiton
Partition 2 - Lots of Gigs, Windows leaves here

But your Windows install is upside down and backwards:

```
Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   238,237,695   [COLOR="Red"]**238,235,648**[/COLOR]   7 HPFS/NTFS
/dev/sda2         238,237,696   245,473,279     [COLOR="Red"]**7,235,584**[/COLOR]   7 HPFS/NTFS
```

The big partition is first, and no 100 meg boot partition is found.  I don't know what the 7 gig 'RAMDRIVE' parttion does:

```
/dev/sda1        274A902DE056554D                       ntfs       SYSTEM                        
/dev/sda2        40388943388938C4                       ntfs       [COLOR="Red"]**RAMDRIVE**[/COLOR] 
```

Were you forced to do some creative things to install Ubuntu on the laptop? It sorta looks that way.

**So: Is the laptop Running XP, Vista or Windows 7?  I need to know for sure so we can correct the situation (XP fix is different from Vista/Win7 fix).**

***The Hedge***

:KS

---

### Post by EarthBoundX5 on 2011-04-10
> **Hedgehog1 said:**
> The big partition is first, and no 100 meg boot partition is found.  I don't know what the 7 gig 'RAMDRIVE' parttion does:

Were you forced to do some creative things to install Ubuntu on the laptop? It sorta looks that way.

**So: Is the laptop Running XP, Vista or Windows 7?  I need to know for sure so we can correct the situation (XP fix is different from Vista/Win7 fix).**

From my understanding the 100 mb partition was only important for bitlocker, regardless I had deleted the 100 mb partition and moved my other partitions over in their place, as I wanted to triple boot 3 OSs and there is the whole 4 primary limit and I did not want to do any extended.

Then came the fun of me not wanting grub and to keep the windows 7 bootmgr....which was fine until out of the blue it stopped booting Ubuntu.  So I gave up and installed Grub, alot of things happened that I don't quite remember....I zeroed the partition table accidentally....fixed it because luckily I had a backup from before I installed my 3rd OS.

Oh and ya, I have Windows 7.

EDIT: and the "RAMDRIVE" is more or less my swap partition for Windows.  Its just to keep my Pagefile on a separate partition.

---

### Post by Hedgehog1 on 2011-04-10
My grandfather ran the TV and Applicance store in Casper, Wyoming *many **MANY*** years ago.  My Dad (as a youth) learned repair of all the equipment they sold.

They had a sign that read this way :p :

```
Standard Rates:
TV Repair (Basic) - $20
TV Repair (If you watch) - $30
TV Repair (If you help) - $50
TV Repair (If you did it first) - $100
```

Now unlike TV repair, trying Disk Partitioning yourself is an important part of mastering these skills:

[IMG]http://img97.imageshack.us/img97/8240/deathparionshishdd.png[/IMG]

So, enough humor (*I hope I can resist!*).

This means that to get your Windows 7 to boot without using the rescue CD, you really do need that little 100 gig boot partition back again.  This can be accomplished without reinstalled windows, and still allow you a separate windows partition for the pagefile.sys (swap) file.

The net result will look like this:

**/dev/sda1 Windows 7 - main partition <Boot Flag [B]off**>
/dev/sda2 Windows pagefile.sys (RAMDRIVE) partition
/dev/sda3 Windows Boot Partition (105 megs - NTFS) <Boot Flag **on**>
/dev/sda4 Extended partition to the end of the disk
__/dev/sda5 ext4 '/' Ubuntu Partiton
__/dev/sda6 Linux Swap[/B]

This means not moving /dev/sda1, /dev/sda4, /dev/sda5 or /dev/sda6.

Instead, the current /dev/sda2 gets shunk by 106 megs, and a new /dev/sda3  of 105 megs is created (NTFS).

Please set the 'boot flag off' on /dev/sda1, and the 'boot flag on' on /dev/sda3. ***Then*** use the Windows rescue CD to populate /dev/sda3.


***The Hedge***

:KS

---

### Post by EarthBoundX5 on 2011-04-12
Problem is...I am 85% sure Windows Booted after I removed said partition (not immediately, I did off course do some screwing around I believe)...

---

### Post by Hedgehog1 on 2011-04-12
Perhaps the very best option is a clean reinstall of both windows and Ubuntu on the laptop...

Of course, that is the non-nerd solution....

But it has some merit...

Honestly, it is your laptop and completely your choice. :P

***The Hedge***

:KS

p.s. If you opt for a clean install of Windows 7 & Ubuntu, a layout like this will give you the least pain and suffering:

[B]/dev/sda1 NTFS 100 meg boot partition (installed by Windows 7)
/dev/sda2 NTFS windows OS (installed by Windows 7, C: Drive)
/dev/sda3 NTFS shared partiton (movies, music, photos, D: Drive)
/dev/sda4 Extended to end of drive
__/dev/sda5 ext4 '/' root
__/dev/sda6 ext4 '/home'
__/dev/sda7 Swap (Size of RAM + 10%)[/B]

---

### Post by EarthBoundX5 on 2011-04-19
Sorry for slow response, I will probably just reformat over the summer, lol; just too busy with classes atm.

---

