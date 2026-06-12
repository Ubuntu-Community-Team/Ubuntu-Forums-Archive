---
title: "Adding Suse 9.1 to Grub2"
date: 2011-07-20
forum: General Help
---

### Post by FreaK2k on 2011-07-20
So, can anybody give me the 40_custom configuration I need?

Suse is not listed in Grub2

It is installed at /dev/sda3/

The Bootloaderentry within Suse (Yast Config shows me this informations)

(hd0,0) vmlinuz root=/dev/hda3 vga=normal apic showopts
(hd0,0) /initrd

Thanks in advance :)

---

### Post by coffeecat on 2011-07-20
Hi. This bit seems a bit odd:

> **FreaK2k said:**
> (Yast Config shows me this informations)

(hd0,0) vmlinuz root=/dev/hda3 vga=normal apic showopts
(hd0,0) /initrd

...because (hd0,0) in legacy grub is not the same as sda3 (hda3), and legacy grub stanza for the kernel line would be something like:

```
kernel   vmlinuz root=....
```

But I always found Yast to be a bit odd anyway. :wink:

To create a 40_custom stanza we need the UUID and filesystem of the Suse partition. I believe Suse used Reiserfs back in 9.* days. Post the output of:

```
sudo blkid
```

By the way - Suse 9.1? Is this for a museum? :)

---

### Post by FreaK2k on 2011-07-20
```
/dev/sda1: UUID="20bfcbd8-d41c-4d8f-957c-14be951939f0" TYPE="ext2" 
/dev/sda2: TYPE="swap" 
/dev/sda3: UUID="3a3333e5-7f47-4505-90c9-f7d5c93988c6" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="547920c8-82e9-40c8-9c29-1b63299aad43" TYPE="ext4" 
/dev/sda6: UUID="262e4d98-6114-4195-bb85-26fc816351e3" TYPE="swap" 

```

And about the museum Question:
YES!!! It's the os an old Software for managing patients is running on it. I have to switch to another Programm (much more comfortable)

---

### Post by coffeecat on 2011-07-20
OK. Try this is 40_custom:

```
menuentry 'Suse 9.1' {
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 3a3333e5-7f47-4505-90c9-f7d5c93988c6
	linux	/boot/vmlinuz root=UUID=3a3333e5-7f47-4505-90c9-f7d5c93988c6 vga=normal apic showopts
	initrd	/boot/initrd
}
```

If that doesn't work, for whatever reason, see if you can access the /boot/grub/menu.lst file in Suse 9.1 and post the contents of that. As I mentioned before the Yast information is a bit odd - for example, an initrd image is usually "initrd.img" rather than just "initrd", but it could be that that was what Suse did then.

If Suse doesn't have a menu.lst, have a look for /boot/grub/grub.conf, which was the alterntive filename for the legacy grub config/menu file.

---

### Post by FreaK2k on 2011-07-20
So didn't work,

This is the Content of the menu.lst from suse.
```
# Modified by YaST2. Last modification on Fri May 14 12:32:34 2004


color white/blue black/light-gray
default 0
timeout 5
gfxmenu (hd0,0)/message

###Don't change this comment - YaST2 identifier: Original name: linux###
title Linux starten
    kernel (hd0,0)/vmlinuz root=/dev/hda3 vga=normal apic showopts
    initrd (hd0,0)/initrd

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Linux im abgesicherten Modus starten
    kernel (hd0,0)/vmlinuz root=/dev/hda3 showopts ide=nodma apm=off acpi=off vga=normal noresume nosmp noapic maxcpus=0  3
    initrd (hd0,0)/initrd

###Don't change this comment - YaST2 identifier: Original name: floppy###
title Von Diskette booten
    root (fd0)
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name: linux###
title Hauptspeichertest
    kernel (hd0,0)/memtest.bin
```

What I found out is, that the company installed an extra /boot Partition. Should be the 1. UUID. The boot folder in the normal Suse installation is empty, but there's a 25mb partition containing the Grubfiles .

---

### Post by coffeecat on 2011-07-20
Yes, of course - separate boot partition. I should have realised. #-o

I'm a bit busy at the moment, but I'll get back to you in an hour or so when I'm not distracted and less likely to make mistakes. :)

---

### Post by FreaK2k on 2011-07-20
Thanks in advance !

---

### Post by coffeecat on 2011-07-20
I avoid boot partitions like the proverbial plague so I don't think I've ever set up a 40_custom stanza for a system with a separate boot partition and I'm not 100% sure this is right, but give it a try:

```
menuentry "Suse 9.1" {
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 20bfcbd8-d41c-4d8f-957c-14be951939f0
	linux	/vmlinuz root=UUID=3a3333e5-7f47-4505-90c9-f7d5c93988c6 vga=normal apic showopts
	initrd	/initrd
}
```

Apart from the different UUID in the search line, I've removed "/boot" from the linux and initrd lines because I can see from your menu.lst that they are both in the root of the filesystem of the sda3 partition - they must be symlinks.

---

### Post by FreaK2k on 2011-07-20
Thank you so much!

Problem solved.
By the way, I don't understand the separated boot Partition. Isn't this only useful, when you experiment with unsupportet filsystems and bootloaders?... But this company is generally a bunch of *****.

Once again, THANK YOU.
This is the reason why I love Ubuntu :)

---

### Post by coffeecat on 2011-07-20
> **FreaK2k said:**
> Thank you so much!

Problem solved.

I'm glad to hear it!

> **FreaK2k said:**
> By the way, I don't understand the separated boot Partition. Isn't this only useful, when you experiment with unsupportet filsystems and bootloaders?... But this company is generally a bunch of *****.

Unsupported filesystems, yes. One other important reason that is relevant to some older machines is when the capacity of the hard drive exceeds the ability of the BIOS to read beyond a certain point - 137GB, if I remember correctly. If you have no boot partition and a kernel upgrade places the new kernel image in the root partition beyond the 137GB point, you have an unbootable system. The way round that is to have a small boot partition at the beginning of the drive so that all the files needed for booting are always within the area that the BIOS can see.

Good luck!

---

