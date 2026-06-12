---
title: "Lost my grub somehow"
date: 2011-02-26
forum: General Help
---

### Post by Julian Luna on 2011-02-26
Help
My ubuntu named "julian" stopped booting with the error:

error: no such partition
grub rescue >

I installed a new ubuntu so I can try better to fix the julian SO's grub
The one I want is at dev/sda6

I did this
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

I marked as bootable my partition from "System -> Administration -> Disk utilities" But it keeps in "Loading"

I did this:
1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4.  Type "root (hd0,6)", or whatever your harddisk + boot partition numbers  are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).
5. Type "setup (hd0)", ot whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot.       

now what? :(
Edit: If I install back over my ubuntu that I want to load which is in /dev/sda6 will it respect my drivers if I don't check "Format partition"?

---

### Post by kiyop on 2011-02-26
What version is Ubuntu LiveCD? 10.10?
What version of grub does your LiveCD use?

What version of grub does your installed ubuntu use?

$ grub-install -v
will show the version.

[quote=Julian Luna #1]3. Type "grub"
4.  Type "root (hd0,6)", or whatever your harddisk + boot partition  numbers  are (my /boot is at /dev/sda7, which translates to hd0,6 for  grub).
5. Type "setup (hd0)", ot whatever your harddisk nr is.
6. Quit grub by typing "quit".[/quote]
is about Grub legacy  (0.9....)

The current version of Ubuntu (10.10) has Grub 2 (Grub 1.9...)

If you use Grub2, please read:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

If you have separate boot(/boot) partition from root(/) partition,
```
sudo fdisk -l
```in order to confirm that your boot partition is /dev/sda7.
```
sudo umount -l /dev/sda7
sudo mkdir -p /mnt/boot
sudo mount /dev/sda7 /mnt/boot[FONT=monospace]
[/FONT]sudo grub-install --root-directory=/mnt /dev/sda
```If grub legacy (grub 0.9...) is used in your installed ubuntu and your LiveCD uses Grub 2, you may have to do complex things. I do not know well.

---

