---
title: "Multiple iso files on a flash drive"
date: 2012-04-28
forum: General Help
---

### Post by rmcellig on 2012-04-28
Is it possible to put multiple iso files of distros on a flash drive and install them that way to my computer rather than burning CD's all the time?

---

### Post by jockyburns on 2012-04-28
Dunno about the feasibility of putting 2 or more distro's on the same flash drive. There must be files that are common to each distro, so might not work.
 Have you considered using individual USB's for each distro? I know it's a bit more expensive than CD's or DVD's. but certainly a lot quicker.

---

### Post by eplc on 2012-04-28
Have a look at YUMI [http://www.pendrivelinux.com/yumi-multiboot-usb-creator/](http://www.pendrivelinux.com/yumi-multiboot-usb-creator/) 

Unfortunately it's for windows, I'm afraid I don't know of a linux equivalent :(

---

### Post by xyzzyman on 2012-04-28
[http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/](http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/)

I use it and I keep ubuntu, fedora & backtrack, along with hirens boot cd all on an 8gb sd card in my reader slot on my notebook. Very handy. Haven't burned a CD or DVD in years by using unetbootin for single distro's and now this to do multiple on one usb/sd card.

---

### Post by codemaniac on 2012-04-28
Multisystem is an lifesaver tool, that works similar to Windows based MultiBootISOs USB creator, and is created for use within Linux.
[http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/](http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/)

---

### Post by Habitual on 2012-04-28
[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)

---

### Post by xyzzyman on 2012-04-28
> **codemaniac said:**
> Multisystem is an lifesaver tool, that works similar to Windows based MultiBootISOs USB creator, and is created for use within Linux.
[http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/](http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/)

That's what I said! lol

---

### Post by surfer on 2012-04-28
i just install grub on the flash drive, copy the isos there and use grub.cfg lines such as

```

menuentry "ubuntu-12.04-desktop-amd64.iso" { 
 set isofile="/iso/ubuntu-12.04-desktop-amd64.iso"
 loopback loop $isofile
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noeject noprompt --
 initrd (loop)/casper/initrd.lz
}


menuentry "ubuntu-12.04-desktop-i386.iso" { 
 set isofile="/iso/ubuntu-12.04-desktop-i386.iso"
 loopback loop $isofile
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noeject noprompt --
 initrd (loop)/casper/initrd.lz
}

```

this works for me.

---

### Post by oldfred on 2012-04-28
I did it surfer's way before many of the scripts that automate the process became available.

If you have mulitiple hard drives you can also install the ISO to another partition and install from that. I have both multiple install ISOs on a flash drive, another flash drive with repair type ISOs and now use primarily another hard drive with ISO.

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

Hard drive:
Direct boot on hard drive - drs305:
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

---

