---
title: "Multiple WUBI installs?"
date: 2011-08-08
forum: General Help
---

### Post by robheus on 2011-08-08
Can one make multiple Wubi installs, and if not, is it possible to change from one Wubi installation to another (for example by exchanging the root.disk file under Windows with one of another Wubi installation)?

The reason I ask is that I have several old installations of Wubi, and I want to be able to use these old installations.

Alternatively, is it possible to access under Ubuntu old root.disk files?

In one occasion my file system got completely full and I was unable to use the filesystem, I want to be able to retrieve some of the files on the filesystem.

---

### Post by oldfred on 2011-08-08
I do not know wubi but have this info I had saved.

How-to: Recover files from Wubi install with LiveCD
[http://neosmart.net/forums/showthread.php?t=5004](http://neosmart.net/forums/showthread.php?t=5004)
[Script] Mount Wubi Disk from Linux mount old wubi in new install
mount ntfs partition first:
[http://ubuntuforums.org/showthread.php?t=1037874](http://ubuntuforums.org/showthread.php?t=1037874)
mkdir /mnt/windows
mount -o loop /mnt/windows/ubuntu/disks/root.disk /mnt/ubuntu

From grub you can manually boot it or possible add a boot stanza to grub.
set Path=/ubuntu/disks/root/disk
search -f --set=Root ${Path} 
probe -u (${Root})  --set=UUID   
linux /vmlinuz root=UUID=${UUID} loop=${Path}  ro
initrd /initrd.img
boot

You might want to try something like this:
HOW TO Avoid Wubi & Install Ubuntu on USB Drive -amjjawad
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)

---

### Post by Frogs Hair on 2011-08-08
To be honest this is the first I have heard of multiple Wubi installations . If you have the Linux kernel images associated with those installations still listed in grub it may be worth a try .

I really don't know if the installations would simply over-write the next in the same space . Look at your system monitor in Ubuntu and see if the space occupied by those installations shows up or only the space occupied by the current installation is there .

---

### Post by oldfred on 2011-08-08
See also this thread, you technically do not need windows to use wubi.

Posts by meierfra. to use grub2 to directly boot wubi
[http://ubuntuforums.org/showthread.php?p=8903013](http://ubuntuforums.org/showthread.php?p=8903013)

But I really recommend full installs if you want to multiboot.

---

