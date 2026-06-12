---
title: "Parted Magic and syslinux"
date: 2010-04-10
forum: General Help
---

### Post by krige on 2010-04-10
In the following instructions:
[http://partedmagic.com/documentation/130-creating-the-liveusb.html](http://partedmagic.com/documentation/130-creating-the-liveusb.html)
it is stated that Ubuntu comes with an old version of syslinux which doesn't work with Parted Magic, so it is suggested to install the newest version available at the follow address:
[http://www.kernel.org/pub/linux/utils/boot/syslinux/](http://www.kernel.org/pub/linux/utils/boot/syslinux/)

How do I check the version of syslinux installed on my system? Why Ubuntu comes with an outdated version of syslinux? How do I install the newest version?

---

### Post by cogier on 2010-04-10
Looks to me like you want to create a bootable Ubuntu on USB stick. If this is the case download a Ubuntu ISO image from [http://www.ubuntu.com/getubuntu/download]("http://www.ubuntu.com/getubuntu/download"). Then go to **System>Administration>USB Startup Disk Creator** (Ubuntu 9.10) and follow the instructions. You will need a USB stick with at least 2GB of memory.

I don't suggest you download software other than through the **Ubuntu Software Centre**

---

### Post by krige on 2010-04-10
Thank you cogier but what I wanted is to have an application like GParted or Parted Magic to boot from a USB drive.

I tried using Startup Disk Creator and UNetbootin but none of them worked.

---

### Post by cogier on 2010-04-10
GParted will not run without Linux. You could use one of the small Linux distros.

---

### Post by krige on 2010-04-10
I was using gparted-live-0.5.2-1.iso available at:
[http://sourceforge.net/projects/gparted/files/gparted-live-stable/](http://sourceforge.net/projects/gparted/files/gparted-live-stable/)
I thought that had integrated some small Linux distro. What would be the use of the iso otherwise?

---

### Post by oldfred on 2010-04-10
I just copied a bunch of ISO to my USB and can boot them. (They have to be set up to allow it)

MultiBoot USB with Grub2 (boot directly from iso files)
[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)

---

### Post by krige on 2010-04-11
> **oldfred said:**
> I just copied a bunch of ISO to my USB and can boot them. (They have to be set up to allow it)

MultiBoot USB with Grub2 (boot directly from iso files)
[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)

Wow, that would be great if I could make it work!

I meticulously followed the instructions I have found on the site you mentioned, but still can't boot from USB.

I am start thinking there may be something wrong with the USB drive. I have opened it with GParted and have noticed it has the "boot" flag only: should any other flag (lba, lvm, etc) be selected?

Also, "fdisk -l" gives me about it the following information:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1        1023     3964094    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(1023, 124, 62) logical=(1022, 124, 62)

```

Is it normal for it to have different physical/logical endings?

---

### Post by cheffabe on 2010-04-13
> **krige said:**
> Is it normal for it to have different physical/logical endings?

I think it is nothing to worry about. My stick formated by Windows shows a similar result. Deleting the partition and setting a new one with gparted (Option: Round to cylinders) fixed that for me.

---

### Post by cheffabe on 2010-04-13
> **krige said:**
> 
How do I check the version of syslinux installed on my system? Why Ubuntu comes with an outdated version of syslinux? How do I install the newest version?

Good questions! I was wondering the same, since it is already updated in debian/testing. There's already a bug about that in launchpad but I don't think there will be a fix soon. :( I think the reason why is because there a patches used with the ubuntu version.

I walked the same path as you did: From pmagic to syslinux. I didn't want to use the syslinux.deb from the debian repros, so I tried to compile it locally. What can I say? I failed since it is more than just a "make install". They use nasm and I'm stuck there.

How far did you get with the Grub-Mulitboot? Did you get the grub boot menu? What was the result of ```
grub-install [COLOR=#660033]--no-floppy[/COLOR] [COLOR=#660033]--root-directory[/COLOR]=[COLOR=#000000]**<usb-mount> /dev/sdX**[/COLOR]
```?

---

### Post by srs5694 on 2010-04-13
> **krige said:**
> Is it normal for it to have different physical/logical endings?

The Master Boot Record (MBR) partitioning scheme attempts to store partition start and end points in two ways:


[list]
[*]Using a cylinder/head/sector (CHS) triplet, which maxes out at about 8GiB
[*]Using a logical block addressing (LBA) scheme, which maxes out at 2TiB
[/list]


The message you note says that these two values don't match. This is most likely caused by either a bug in the original partitioning software or a different interpretation of the disk's CHS geometry (that is, how many cylinders and heads it supports) by the original partitioning software vs. fdisk.

The danger here is that two different OSes or low-level utilities will use different values (one using CHS and the other LBA), or that they'll both use CHS but interpret the CHS geometry differently. The result will be inconsistencies in the start and/or end points of the partition(s) on the disk, which in turn will lead to problems. Most likely the problems would manifest as an inability to mount the partition in one OS, but there could be more serious issues. For instance, an attempt to fix what appears to be a corrupt filesystem because of varying interpretations could end up harming it.

That said, my impression is that most modern OSes favor the LBA values; the CHS values are present mostly for historical purposes. Certainly the CHS values are useless on any disk over 8GiB in size. To completely eliminate the chance of misinterpretation, you could convert the disk to use the GUID Partition Table (GPT) instead of MBR; GPT doesn't use CHS values at all, only LBA values.

---

### Post by krige on 2010-04-13
Hey cheffabe, thanks for the support!

First I tried deleting the partition (I didn't think about that) and setting a new one with gparted (Option: Round to cylinders), repeated the procedure MultiBootUSB installation procedure but that didn't work out either :(

This is what I have done:

```
sudo mkfs.vfat -n MultiBootUSB /dev/sdb1
# mkfs.vfat 3.0.7 (24 Dec 2009)

sudo mount /dev/sdb1 /mnt/

sudo grub-install --no-floppy --root-directory=/mnt /dev/sdb
# Installation finished. No error reported.

sudo vim /mnt/boot/grub/grub.cfg

# --- pasted into it the following ---

menuentry "GParted" {
 loopback loop /boot/iso/gparted-live-0.5.2-1.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/iso/gparted-live-0.5.2-1.iso noeject noprompt --
 initrd (loop)/casper/initrd.lz
}
 
menuentry "Parted Magic" {
 loopback loop /boot/iso/pmagic-4.10.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/iso/pmagic-4.10.iso noeject noprompt --
 initrd (loop)/casper/initrd.lz
}

# ---------------------------

sudo mkdir /mnt/boot/iso

sudo cp gparted-live-0.5.2-1.iso /mnt/boot/iso/

sudo cp pmagic-4.10.iso /mnt/boot/iso/

sudo sync

sudo umount /mnt/

```

---

### Post by krige on 2010-04-13
> **srs5694 said:**
> The Master Boot Record (MBR) partitioning scheme attempts to store partition start and end points in two ways:


[list]
[*]Using a cylinder/head/sector (CHS) triplet, which maxes out at about 8GiB
[*]Using a logical block addressing (LBA) scheme, which maxes out at 2TiB
[/list]


The message you note says that these two values don't match. This is most likely caused by either a bug in the original partitioning software or a different interpretation of the disk's CHS geometry (that is, how many cylinders and heads it supports) by the original partitioning software vs. fdisk.

The danger here is that two different OSes or low-level utilities will use different values (one using CHS and the other LBA), or that they'll both use CHS but interpret the CHS geometry differently. The result will be inconsistencies in the start and/or end points of the partition(s) on the disk, which in turn will lead to problems. Most likely the problems would manifest as an inability to mount the partition in one OS, but there could be more serious issues. For instance, an attempt to fix what appears to be a corrupt filesystem because of varying interpretations could end up harming it.

That said, my impression is that most modern OSes favor the LBA values; the CHS values are present mostly for historical purposes. Certainly the CHS values are useless on any disk over 8GiB in size. To completely eliminate the chance of misinterpretation, you could convert the disk to use the GUID Partition Table (GPT) instead of MBR; GPT doesn't use CHS values at all, only LBA values.

Thank you srs5694, both for the explanation and suggestion.

I did what cheffabe suggested: deleted the partition and created a new one with GParted. Now fdisk -l shows the following without any other message:
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         493     3959991    b  W95 FAT32
```

Doing this didn't fix my problem though, still it doesn't boot from USB. Do you suggest anyway to try converting the disk to use the GUID Partition Table (GPT) instead of MBR? If yes, how do I do that?

---

### Post by srs5694 on 2010-04-13
> **krige said:**
> Doing this didn't fix my problem though, still it doesn't boot from USB. Do you suggest anyway to try converting the disk to use the GUID Partition Table (GPT) instead of MBR? If yes, how do I do that?

I'd forgotten you were trying to create a bootable disk. I know relatively little about syslinux, and in particular I don't know if it's GPT-friendly. I therefore wouldn't try such a conversion unless you research that issue further and find that it should work. If you do, you can use [GPT fdisk](http://www.rodsbooks.com/gdisk) to do the conversion.

---

### Post by cheffabe on 2010-04-13
I think your grub.cfg is wrong for the stuff your trying to boot. casper? is that for ubuntu itself? I suggest something like this:

```
menuentry "tinycore" {
 loopback loop /iso/tinycore_2.10.iso
 linux (loop)/bzImage --
 initrd (loop)/tinycore.gz
}

menuentry "pmagic" {
 loopback loop /iso/pmagic-4.10.iso
 linux (loop)/pmagic/bzImage edd=off noapic load_ramdisk=1 prompt_ramdisk=0 rw loglevel=0 vga=791 livemedia noeject max_loop=256 keymap=us
 initrd (loop)/pmagic/initramfs
}

```I tested the tinycore one, Im not sure with pmagic. You can remove all kernel options (line starting with linux) for starters. Good Luck. You definitely need to see the grub menu with all your menu entries first in order to verify that grub2 is starting. (Check Bios settings!!)

For the menuentries you can mount the isos and verify the boot options in there.

---

### Post by oldfred on 2010-04-13
I have not yet tested all the Ubuntu versions but all the rest worked- my grub.cfg on my USB key:
```

menuentry "Ubuntu 10.04 64bit" {
    set isofile="/boot/ISOs/lucid-desktop-amd64.iso"
 
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile
    initrd (loop)/casper/initrd.lz
}

menuentry "Ubuntu 9.10 64 bit" {
    set isofile="/boot/ISOs/ubuntu-9.10-desktop-amd64.iso"
 
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt --
    initrd (loop)/casper/initrd.lz
}

menuentry " " {
set root= 
}

menuentry "Ubuntu 9.10 32 bit" {
    set isofile="/boot/ISOs/ubuntu-9.10-desktop-i386.iso"
 
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt --
    initrd (loop)/casper/initrd.lz
}

menuentry "Ubuntu 9.04 32 bit" {
    set isofile="/boot/ISOs/ubuntu-9.04-desktop-i386.iso"
 
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt --
    initrd (loop)/casper/initrd.gz
}

menuentry "Parted Magic" {
    set isofile="/boot/ISOs/pmagic-4.8.iso"

    loopback loop $isofile 
    linux (loop)/pmagic/bzImage iso_filename=$isofile edd=off noapic load_ramdisk=1 prompt_ramdisk=0 rwnomce sleep=10 loglevel=0
    initrd (loop)/pmagic/initramfs
}

menuentry " " {
set root= 
}

menuentry "SystemRescueCd 1.5.0" {
 set isofile="/boot/ISOs/systemrescuecd-x86-1.5.0.iso"
 loopback loop $isofile 
 linux (loop)/isolinux/rescuecd isoloop=$isofile  
 initrd (loop)/isolinux/initram.igz
}

menuentry "Gparted live" {
  insmod loopback
  insmod iso9660
  set gfxpayload=800x600x16, 800x600
  set isofile="/boot/ISOs/gparted-live-0.5.2-1.iso"
  loopback loop $isofile
  linux (loop)/live/vmlinuz boot=live union=aufs noswap noprompt ip=frommedia toram=filesystem.squashfs findiso=$isofile
  initrd (loop)/live/initrd.img
}


menuentry "gparted (Boot ISO Image via Grub2) "{
        set isofile="/boot/ISOs/gparted-live-0.5.2-1.iso"
    loopback loop $isofile 
    linux (loop)/live/vmlinuz live-media=iso=$isofile keyb=us gl_kbd=us gl_lang=en_US gl_numlk=off gl_batch          boot=live union=aufs  toram=filesystem.squashfs noswap noprompt 
    initrd (loop)/live/initrd.img
}

menuentry " " {
set root= 
}

menuentry "Reboot" {
    reboot
}

menuentry "Halt" {
    halt
}

menuentry "Memory test (memtest86+)" {
 linux /boot/memtest86+.bin
}
```

---

### Post by C.S.Cameron on 2010-04-20
Hey Oldfred:
Did you say the menuentrys for gparted are working for you?
Neither seem to work for me. 

Ubuntu goes persistent if I add persistent to the menuentry line as shown below and make a ext2 partition labeled casper-rw.

linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt -- persistent

---

### Post by drs305 on 2010-04-20
I just posted a menuentry in the Grub 2 Basics thread this afternoon for booting the ISO from a hard drive. I was using latest version of the Parted Magic ISO and the menuentry is a bit different than what's been posted here. But apparently they all work.

[Grub 2 Basics]("http://ubuntuforums.org/showthread.php?t=1195275")
Section 14.

---

### Post by oldfred on 2010-04-21
My second gparted starts to boot but sees my several root partitions as FAT and gives a UTF-8 error and loops. I did not intend to include that.

The first gparted entry works but I do see a few messages flash by.
this is the one that worked for me:

menuentry "Gparted live" {
  insmod loopback
  insmod iso9660
  set gfxpayload=800x600x16, 800x600
  set isofile="/boot/ISOs/gparted-live-0.5.2-1.iso"
  loopback loop $isofile
  linux (loop)/live/vmlinuz boot=live union=aufs noswap noprompt ip=frommedia toram=filesystem.squashfs findiso=$isofile
  initrd (loop)/live/initrd.img
}

---

### Post by C.S.Cameron on 2010-04-21
When I try the gparted script I get:
error: file not found
Press any key to continue...

---

### Post by oldfred on 2010-04-21
IS your path & version correct, I did not use ISO but ISOs and just copied the iso file name to make sure the version was correct?

---

### Post by drs305 on 2010-04-22
> **C.S.Cameron said:**
> When I try the gparted script I get:
error: file not found
Press any key to continue...

I just downloaded the current gparted iso and this works for me. in my case, the file is on sda6 in the /apps folder:

```

menuentry "Gparted live" {
loopback loop (**hd0,6**)**/apps/**gparted-live-0.5.2-1.iso
linux (loop)/live/vmlinuz boot=live union=aufs noswap noprompt ip=frommedia **findiso=/apps/**gparted-live-0.5.2-1.iso  toram=filesystem.squashfs 
initrd (loop)/live/initrd.img
}

```

---

### Post by C.S.Cameron on 2010-04-22
Well dang,
Who would have ever guessed that the path had to be right!
Thanks.

Any suggestions to get NimbleX working?
The best I can get so far is:

"error: You need to load the kernel first.
Press any key to continue..."

---

