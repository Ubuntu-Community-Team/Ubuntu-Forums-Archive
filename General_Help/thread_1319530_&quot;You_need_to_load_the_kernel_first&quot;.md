---
title: "&quot;You need to load the kernel first&quot;"
date: 2009-11-08
forum: General Help
---

### Post by Jordanwb on 2009-11-08
I installed Grub2 to a 1GB flash drive and put the 9.10 Minimal iso on it and put the following in /boot/grub/grub/cfg:

```
menuentry "Kubuntu Live 9.10 64bit" {
 loopback loop /boot/iso/kubuntu-9.10-desktop-amd64.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/iso/kubuntu-9.10-desktop-amd64.iso noeject noprompt quiet splash
 initrd (loop)/casper/initrd.lz
}

menuentry "Ubuntu Minimal 9.10 64bit" {
 loopback loop /boot/iso/ubuntu-9.10-minimal-amd64.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/iso/ubuntu-9.10-minimal-amd64.iso noeject noprompt quiet
 initrd (loop)/casper/initrd.lz
}

```

Booting Kubuntu from the flash drive works just fine, but when I try to load the Minimal "CD" I get an error saying that I need to load the kernel first. I get the same error with 9.04 releases.

*Edit* Dammit, the minimal CD doesn't have the same file structure as the other releases. Well played Canonical, well played. <_<

---

### Post by sisco311 on 2009-11-08
download the kernel(vmlinuz) and the initial ramdisk(initrd.gz) from: [http://archive.ubuntu.com/ubuntu/dists/karmic/main/installer-amd64/current/images/hd-media/]("http://archive.ubuntu.com/ubuntu/dists/karmic/main/installer-amd64/current/images/hd-media/")

edit the grub entry to something like:
```
menuentry "Ubuntu Minimal 9.10 64bit" {
 set root=(hd...)
 linux /boot/vmlinuz root=UUID=.....
 initrd /boot/initrd.gz
}
```

If the installer doesn't find the iso, then copy it to the root of the partition.

Manual editing of grub.cfg is not encouraged, add the entries to /etc/grub.d/40_custom

[thread=1195275]The Grub 2 Guide[/thread]

---

### Post by Jordanwb on 2009-11-08
> **sisco311 said:**
> Manual editing of grub.cfg is not encouraged, add the entries to /etc/grub.d/40_custom

I installed grub2 to a flash drive, so when update-grub is called, grub2 which is on my flash drive is not affected.

---

### Post by fermulator on 2010-10-27
Same problem here.

Was trying to do something like: [http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)

---

