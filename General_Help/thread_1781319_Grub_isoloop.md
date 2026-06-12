---
title: "Grub isoloop"
date: 2011-06-13
forum: General Help
---

### Post by mightyiam on 2011-06-13
Dear Friends,

A USB Flash is formatted is MBR formatted, one primary partition with FAT32.

In there, I put the four different Ubuntu CD images:
```

shahar@shahar-desktop:~$ ls -l /media/SHAHAR_SYST/operating-systems/
total 2843060
-rw-r--r-- 1 shahar shahar 733849600 2011-04-26 15:58 ubuntu-11.04-alternate-amd64.iso
-rw-r--r-- 1 shahar shahar 726740992 2011-05-21 16:27 ubuntu-11.04-alternate-i386.iso
-rw-r--r-- 1 shahar shahar 732112896 2011-05-03 13:34 ubuntu-11.04-desktop-amd64.iso
-rw-r--r-- 1 shahar shahar 718583808 2011-05-03 12:43 ubuntu-11.04-desktop-i386.iso


```

Theres also GRUB2 installed:

```
set timeout=10
set default=0

menuentry "Ubuntu 11.04 Desktop i386 (memtest86+)" {
    set isofile="/operating-systems/ubuntu-11.04-desktop-i386.iso"

    loopback loop $isofile
    linux16 (loop)/install/mt86plus
}

menuentry "Ubuntu 11.04 Desktop i386" {
    set isofile="/operating-systems/ubuntu-11.04-desktop-i386.iso"

    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash --
    initrd (loop)/casper/initrd.lz
}

menuentry "Ubuntu 11.04 Desktop amd64" {
    set isofile="/operating-systems/ubuntu-11.04-desktop-amd64.iso"

    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash --
    initrd (loop)/casperUbuntu 11.04 Alternate amd64
}

menuentry "Ubuntu 11.04 Alternate i386" {
	set isofile="/operating-systems/ubuntu-11.04-alternate-i386.iso"
	set gfxpayload=keep
	loopback loop $isofile
	linux	(loop)/install/vmlinuz  iso-scan/filename=$isofile file=/cdrom/preseed/ubuntu.seed quiet --
	initrd	(loop)/install/initrd.gz
}

menuentry "Ubuntu 11.04 Alternate amd64" {
        set isofile="/operating-systems/ubuntu-11.04-alternate-amd64.iso"
        set gfxpayload=keep
        loopback loop $isofile
        linux   (loop)/install/vmlinuz  iso-scan/filename=$isofile file=/cdrom/preseed/ubuntu.seed quiet --
        initrd  (loop)/install/initrd.gz
}
```

It kinda sorta works. The problem is that it takes a long time from executing the command list in GRUB2 to actual boot. After I press enter on a menu item, I get a long period of waiting with a black screen (don't remember the little text it has - nothing unsusual) before I get to see the kernel doing it's thing. And some times it even takes too long that I'm not sure whether it will eventually boot.

During this time, the LED on the USB stick keeps fading in and out. For what its worth, this is a SanDisk Cruzer 8GB.

I have a feeling that this has to do with the isoloop feature under FAT32 or in general. mainly because this doesn't happen when live system is installed like with unetbootin.

Booting the memtest86+ entry doesn't give any trouble.

Anyone experienced this?

Blessings,
Thanks,
Shahar

---

### Post by zaxxit on 2011-07-15
same problem here, but:
ubuntu 11.04 x86 cd.iso on usb hdd primary partition 1 size 50GB ntfs
grub2 loader

issues: 
- on p4 very slow
- on amd x64 dual core very slow

for now: its not a FAT32 issue

---

### Post by Quackers on 2011-07-15
Have you seen this thread?
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

Also, it's possible to boot some iso's direct from the grub menu - see here
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)

---

