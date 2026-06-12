---
title: "grub2 and ISO files, and Windows 7"
date: 2011-08-25
forum: General Help
---

### Post by Grenage on 2011-08-25
Greetings,

If I format a USB key as NTFS, mark it as bootable and copy over the Windows 7 files (contained in the ISO), it boots as I would expect.  Naturally, a simple job ends up branching off into irrelevant projects, and that's really what this is.

It's a large USB drive, so I decided to store multiple images and configure grub2 so that I could choose which OS to install; I've no doubt that many people here have done the same thing.  It turns out that ISO support is available, so I've added several image files, and that also works.  Here's the top two items:

```
menuentry "Ubuntu 11.04 AMD64" {
	loopback loop /boot/iso/ubuntu-11.04-amd64.iso
	linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/iso/ubuntu-11.04-amd64.iso noeject noprompt --
	initrd (loop)/casper/initrd.lz
}

menuentry "Windows 7 Ultimate N AMD64" {
	set root=(hd0,2)
	chainloader +1
}
```

Windows wouldn't boot from the ISO file, but I wasn't really expecting it to work, so I replaced that entry with the above.  I created a second primary partition and extracted the Windows 7 ISO files exactly as I did when it was on its own USB drive.  That also failed, but with a Windows "the boot selection failed because a required device is inaccessible".

My understanding is that chainloader will direct the system to a boot record on the referenced partition/drive, and as I actually get as far as a *Windows* error message, I'm not sure why it's not working.

Has anyone else made something similar?

---

### Post by bodhi.zazen on 2011-08-25
This is an Ubuntu forums and we are directing non-Ubuntu support to a more appropriate location.

Examples would include Fedora questions -> Fedora forums
mint questions -> mint forums
debian -> debian
etc


In your case that would either be Microsoft, a windows forums, or the grub mailing list.

---

