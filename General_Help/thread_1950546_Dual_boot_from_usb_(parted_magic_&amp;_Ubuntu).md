---
title: "Dual boot from usb (parted magic &amp; Ubuntu)"
date: 2012-03-31
forum: General Help
---

### Post by tealio on 2012-03-31
I have Ubuntu installed on a USB flash drive, and parted magic was previously installed to the USB using YUMI. I need to be able to dual boot these from the USB or have the option to boot the mbr of the hd which contains windows. I'm not opposed to starting completely over, but I'd like to be able to configure grub to accomplish this. I have to leave the mbr of the hd alone and have the option to boot the hd even if I boot with the USB device inserted. Thanks in advance.

---

### Post by oldfred on 2012-04-01
I would use grub2 and just copy the ISO to the flash drive. Then add a boot stanza for booting the internal drive also.

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB")

You may have to adjust some of these entries to your versions or partitions, this is part of my grub2.cfg from my USB flash drive. I copy ISOs to /boot/iso. Drive often mounts as sdd, but I am changing that /dev/sdd to hd0.

```
set default=0 
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue
set gfxpayload=800x600

menuentry "Ubuntu 11.10 Oneiric 64bit" {
    set isofile="/boot/iso/oneiric-desktop-amd64.iso"
    loopback loop (/dev/sdd,msdos1)/$isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset noprompt
    initrd (loop)/casper/initrd.lz
}

menuentry " " {
set root= 
}

# iso_filename=$isofile boot=live load_ramdisk=1 prompt_ramdisk=0 noeject noprompt 
menuentry "Parted Magic 6.1" {
    set isofile="/boot/iso/pmagic-6.1.iso"
    loopback loop $isofile 
    linux (loop)/pmagic/bzImage iso_filename=$isofile edd=off noapic load_ramdisk=1 prompt_ramdisk=0 rw loglevel=0 max_loop=256
    initrd (loop)/pmagic/initramfs
}
menuentry " " {
set root= 
}

menuentry "Windows (loader) (on /dev/sda2)" {
insmod ntfs
set root=(hd0,2)
chainloader +1
}
# Note boot drive is normally hd0, next drive will be hd1 even if sda
menuentry "boot to first mbr"{
set root=(hd0)
chainloader +1
}

menuentry "Reboot" {
    reboot
}

```

---

### Post by tealio on 2012-04-01
I thought if i directly edited grub.cfg the changes would be wiped out the next time *update-grub* is run.  I do already have grub installed to the flash drive, and there are entries for the USB stick, and Windows.

Also, this answer isn't *exactly* what i want.  I'd like an entry in grub (which i think YUMI uses?) that says something like "Boot Primary HD/Partition" that would boot the first drive, first partition on any computer.  As of now, and i think according to the instructions, the grub menu would be specific to having the USB drive inserted in this particular laptop. Maybe i need to check out the YUMI grub.cfg?  

I do appreciate the quick response, and i'm gonna give it a try right now. Results to follow.

---

### Post by tealio on 2012-04-01
OK, so YUMI uses syslinux... Would it maybe be easier to use syslinux, since my Ubuntu install (update-grub) wouldn't destroy changes ?

---

### Post by tealio on 2012-04-01
also, not sure i made it clear, but Ubuntu is INSTALLED on the USB, not running a live iso...

---

### Post by oldfred on 2012-04-01
I do have another flash drive with a full install of Ubuntu on that one I also added some ISO but have to edit 40_custom to have the entries. Most are similar to the one's above.

The entry to boot hd0 will boot the drive that is hd0, but I have found from BIOS/grub the boot drive is always hd0. Then drive order is the order from motherboard SATA ports. It may be different if IDE/PATA.

So when I boot sdb, it is hd0 and sda is hd1, but if I boot sda it is hd0 and sdb is hd1. But a chain entry works in either case (but number may have to be changed), but depending on drive used, sometimes manual entry may be required.

I also have this type of entry to boot a partition: This works with Ubuntu since it puts a link in / (root) to the most current kernel installed.

I first saw this from Ranch hand (I think he was testing and kernels changed a lot).
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition. example based on sda13 change all 13's to your partition number. Description can be anything.

menuentry "Ubuntu on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

But again, note that booting with an USB the hd0 may be hd1 or other depending on drive order. Some systems promote a flash drive to sda, most seem to mount it as the next drive. Best to know how to manually edit grub when it comes back and says not found.

I am not familar with yumi, why are you using that?
Grub2 is the standard boot loader for full installs and syslinux seems to be used by most for small flash drives for ISOs that are instlalled, not copied & loop mounted like I do.

---

### Post by tealio on 2012-04-01
Success! I was headed in the wrong direction using YUMI under windows... I should have just tried the "hard way" to start with!

I noticed a script in /etc/grub.d/ called *41_custom* that basically said if there's a file called /boot/grub/custom.cfg then it should be sourced when making the menu entries.  

I put the ISO in /boot/ISOs and created a menu entry for it, and there you have it.  My grub menu is created the way it should be, and i won't have to change anything when a new kernel is installed and *update-grub* is run.  Thanks for all the help!

When i boot back into Ubuntu (booted into partedmagic right now) i'll post a better description of what i did and mark the thread [SOLVED]

Thanks again.

---

### Post by tealio on 2012-04-04
I ended up formatting the USB and repartitioning, making ubuntu the first partition, and removing the YUMI installations.

Once this was done, it was easy to setup what i wanted to do with grub.

I moved the ISO (parted magic) into a newly created folder called */boot/ISOs* and renamed the iso *pmagic.iso*.

I then created a file in the */boot/grub* directory called *custom.cfg*.  This file (if it exists) is sourced by a script (*/etc/grub.d/41_custom*) that is called by *grub-update*.

Here's the contents of the new */boot/grub/custom.cfg*:
```
menuentry "Parted Magic" {
	set isofile="/boot/ISOs/pmagic.iso"
	loopback loop $isofile 
	linux (loop)/pmagic/bzImage iso_filename=$isofile edd=off noapic load_ramdisk=1 prompt_ramdisk=0 rwnomce sleep=10 loglevel=0
	initrd (loop)/pmagic/initrd.img
}
```

That's all it took.  I haven't been able to "boot through" my USB to Windows, which resides on the HD, but if i "want" Windows i just remove the USB and boot normally.  I've taken the executable bit off of */etc/grub.d/30_os-prober* because the Windows entry it creates doesn't work.

---

