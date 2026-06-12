---
title: "grub entry for booting Ubuntu from USB"
date: 2011-05-13
forum: General Help
---

### Post by xerces8 on 2011-05-13
Hi!

Can someone please post the menu.lst lines for booting ubuntu-11.04-desktop-i386.iso from a USB stick?

I already have grub and the iso on the stick, I just need the two lines for menu.lst.

(I already have ubuntu 10.10 with this lines:


title Ubuntu 10.10 i386
find --set-root /ubuntu-10.10-desktop-i386.iso
map /ubuntu-10.10-desktop-i386.iso (0xff)
map --hook
root (0xff)
kernel /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper iso-scan/filename=/ubuntu-10.10-desktop-i386.iso splash quiet --
initrd /casper/initrd.lz

is it good for 11.04 too or did they change some things?)

Thanks,
David

---

### Post by oldfred on 2011-05-13
I did not know grub legacy worked. I am using grub2 to loop mount ISO.

```
set default=0 
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue
set gfxpayload=800x600


menuentry "Ubuntu 10.10 Maverick 64bit" {
    set isofile="/boot/iso/ubuntu-10.10-desktop-amd64.iso"
 
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset noprompt
    initrd (loop)/casper/initrd.lz
}


menuentry "Ubuntu 11.04 Natty 64bit" {
    set isofile="/boot/iso/natty-desktop-amd64.iso"
 
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset noprompt
    initrd (loop)/casper/initrd.lz
}

menuentry " " {
set root= 
}
```

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

---

### Post by C.S.Cameron on 2011-05-13
My laptop has only been upgraded for the last few years and still uses grub legacy, here is the menu.lst with an entry to boot flash drives:

# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title		Ubuntu 9.10, kernel 2.6.31-17-generic
uuid		63359e62-65d3-42b9-b813-675f9beda772
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=63359e62-65d3-42b9-b813-675f9beda772 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-17-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid		63359e62-65d3-42b9-b813-675f9beda772
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=63359e62-65d3-42b9-b813-675f9beda772 ro  single
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, memtest86+
uuid		63359e62-65d3-42b9-b813-675f9beda772
kernel		/boot/memtest86+.bin
quiet

title		Flash Drive
root		(hd1,0)
savedefault
makeactive
chainloader	+1

---

### Post by _0R10N on 2011-05-13
> **xerces8 said:**
> Hi!

Can someone please post the menu.lst lines for booting ubuntu-11.04-desktop-i386.iso from a USB stick?

I already have grub and the iso on the stick, I just need the two lines for menu.lst.

(I already have ubuntu 10.10 with this lines:


title Ubuntu 10.10 i386
find --set-root /ubuntu-10.10-desktop-i386.iso
map /ubuntu-10.10-desktop-i386.iso (0xff)
map --hook
root (0xff)
kernel /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper iso-scan/filename=/ubuntu-10.10-desktop-i386.iso splash quiet --
initrd /casper/initrd.lz

is it good for 11.04 too or did they change some things?)

Thanks,
David


Excuse me, and correct me if I'm wrong I don't think this is possible. I mean, in order to boot from an USB stick + Ubuntu ISO, you go through the startup disk creator process.

I know that when a PC starts up it looks for the MBR of the Primary Master device, since it won't be your USB stick, I don't see when your USB grub menu.lst file would be read.

---

### Post by wilee-nilee on 2011-05-13
> **_0R10N said:**
> Excuse me, and correct me if I'm wrong I don't think this is possible. I mean, in order to boot from an USB stick + Ubuntu ISO, you go through the startup disk creator process.

I know that when a PC starts up it looks for the MBR of the Primary Master device, since it won't be your USB stick, I don't see when your USB grub menu.lst file would be read.

That is one way, but not relevant other then for your understanding, and anybody else, good question though.:)

You can load a thumb with all the grub components needed to add installs to the menu and boot without a actual install to have the grub menu, and associated files.

You load the thumb with the grub stuff, then load the iso and adjust the menu to boot. oldfred has some great links on this that they posted, and I would suspect C.S. Cameron knows all this stuff to.;)

---

### Post by oldfred on 2011-05-14
I have never done it with old grub legacy, but it looks like you have to extract the kernel & initrd files and boot those and then use that running system to get into the ISO. 

Grub2 has to do the same for some ISO that are not set up to loop mount.

---

### Post by xerces8 on 2011-05-14
> **xerces8 said:**
> 
title Ubuntu 10.10 i386
find --set-root /ubuntu-10.10-desktop-i386.iso
map /ubuntu-10.10-desktop-i386.iso (0xff)
map --hook
root (0xff)
kernel /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper iso-scan/filename=/ubuntu-10.10-desktop-i386.iso splash quiet --
initrd /casper/initrd.lz

I changed the numbers in this to 11.04 and it works.

That's right, _0R10N ;)
10.10 and 10.04 also work this way.

---

