---
title: "CD to Memory Stick"
date: 2009-08-27
forum: General Help
---

### Post by lucast on 2009-08-27
Hi,

I have a System Rescue CD that came with my eeePC 1005HA but I haven't got an external CD drive to use it.  I was wondering if it is possible to copy this to a Memory stick and then be able to boot from it.

My Desktop which has a CD drive is running Ubuntu 9.04.

Any help would be much appreciated.

---

### Post by P4man on 2009-08-27
Maybe this works:

```
dd if=/dev/cdrom1 of=/dev/yourusbstick
```

---

### Post by dandnsmith on 2009-08-27
I don't think it's that simple, as the booting for a CD normally pretends it is something like a floppy.
Creation of bootable linux distros usually involves using syslinux to make the stick bootable.
I cannot immediately expand on this, as a lot depends on the content of the CD, what file is set to be obeyed first, adn what sort of environment it is trying to establish.

Possibly the manufacturer has cought up with progress enough to offer either a USB bootanble version or tips on how to do it.

Why not get a (cheap) external CD drive connected by USB? (I use an old drive, and a cable converter from IDE to USB for this purpose)

---

### Post by P4man on 2009-08-27
I wouldn't bet my life on it either. Maybe it depends on the bios,  but it should generate an USB stick with an ISO9660 file system (so read only). But it should be bootable if the cd is bootable. 

Either way its easy to try.

---

### Post by lucast on 2009-08-27
I will give it a go tonight, like you said I have nothing to loose.  If not, I work next to a computer shop so I will pick up a converter cable as I have several old drives kicking around at home.

I will let you know how I get on tomorrow.

Thanks for your help!

---

### Post by mike555 on 2009-08-27
I have read that some netbooks boot off a USB drive by holding a certain key while booting ........ check your make or you might need to change the boot order in the bios ...

---

