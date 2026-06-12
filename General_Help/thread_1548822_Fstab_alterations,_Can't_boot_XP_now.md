---
title: "Fstab alterations, Can't boot XP now?"
date: 2010-08-08
forum: General Help
---

### Post by Uruz on 2010-08-08
I've got 4 partitions split between 2 drives.

I messed with Fstab, Pysdm and Disk Utility to get the other three (the ones I'm not booting from) to mount automatically and to have specific names. Everything works fine. (except I can't get the mount point names to contain spaces, but oh well)

But when I go to boot from my XP partition (sda5) I get an error! It's extremely generic and doesn't look like it's from Grub or Ubuntu. Could something be wrong with my Grub configuration?

Thanks for the help,
Uruz

**EDIT**
Also, now there is a phantom, unmountable drive in the Computer folder with the same name as one of my mount points. It doesn't do anything and I can't figure out why it's there.

---

### Post by darolu on 2010-08-09
To add spaces use "\" (also works for special characters for example:
```
cd Metallica\ S\ \&\ M/

mkdir /media/Music\ Disk
```
The "phantom" can be your already mounted partition being listed under Places as a device (not mounted of course).

As for the error on your XP partition, you do need to post what is the error you get as it can be GRUB issue; unless it appears after Windows starts booting.

---

### Post by Uruz on 2010-08-09
> **darolu said:**
> To add spaces use "\" (also works for special characters for example:
```
cd Metallica\ S\ \&\ M/

mkdir /media/Music\ Disk
```
The "phantom" can be your already mounted partition being listed under Places as a device (not mounted of course).

As for the error on your XP partition, you do need to post what is the error you get as it can be GRUB issue; unless it appears after Windows starts booting.

Thank you very much.

And I solved the boot problem, somehow boot.ini got destroyed, but that's fixed now.

So, using \, do I just put that and then the space (sorry, I don't really understand from your example)

Also, What can I do to remove the phantom drive (it looks like a cd drive, by the way)?

---

