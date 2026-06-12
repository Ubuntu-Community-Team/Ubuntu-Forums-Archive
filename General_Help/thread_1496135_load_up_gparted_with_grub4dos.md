---
title: "load up gparted with grub4dos?"
date: 2010-05-28
forum: General Help
---

### Post by josephellengar on 2010-05-28
I built a multi-boot flash drive using the instructions [here]("http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/") but unfortunately, those instructions don't include gparted, and I much prefer gparted to the partition managers that are included.  How would I go about loading gparted with grub4dos?  Either the zip or the iso version is okay with me, I just want to be able to load the live version of the program.  I do know that it is included in the ubuntu livecd that I have loaded on the flash drive, but I prefer the standalone version.  Thanks!

---

### Post by garvinrick4 on 2010-05-28
grub4dos is the Windows version of Grub? Are you running a linux version? Does it have
gparted in its repositories? 
Can either download from a repository or Make a Live CD.


[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by josephellengar on 2010-05-29
> **garvinrick4 said:**
> grub4dos is the Windows version of Grub? Are you running a linux version? Does it have
gparted in its repositories? 
Can either download from a repository or Make a Live CD.


[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

I am trying to put gparted on my flash drive.  I chainload grub4dos and then can boot a number of different tools.  It's easier than carrying around a ton of live cds.  Grub4dos is a windows-friendly version of grub which strangely is far more feature packed than the real grub.

---

### Post by josephellengar on 2010-05-29
Solved:

```

title Gparted 0.5.2-9
root (hd0,0)
kernel /gparted/live/vmlinuz live-media-path=gparted/live bootfrom=/dev/sd boot=live union=aufs noprompt ocs_live_run="ocs-live-general" ocs_live_extra_param="" ocs_live_keymap="" ocs_live_batch="no" ocs_lang="" vga=791 ip=frommedia
initrd /gparted/live/initrd.img

```

---

