---
title: "quad booting backtrack, ubuntu 64, windows 7?"
date: 2010-08-03
forum: General Help
---

### Post by capitalfear on 2010-08-03
this is what i want to do when i get a new system76 laptop, and i need backtrack4, ubuntu 64 bit, and windows7 32 bit for my occasional gaming habits. i just need to know what order and everything for a seemless installation. thank you for any suggestions

---

### Post by realzippy on 2010-08-03
This might help:

[http://ubuntuforums.org/showthread.php?t=1508494](http://ubuntuforums.org/showthread.php?t=1508494)

---

### Post by capitalfear on 2010-08-03
im reading this. and so far i must say you are a wonderful human being, thank you

---

### Post by WorMzy on 2010-08-03
You can install them in any order you want, though installing Ubuntu last would make it easier to set up grub, if that's the bootloader you plan to use.

---

### Post by capitalfear on 2010-08-03
okay thanks thats helpful. considering i plan to make ubuntu my primary considering how much i love it :]

---

### Post by Mark Phelps on 2010-08-03
Make note that when you install Win7, it will overwrite the MBR.  NO way around that.

Also, if you install; Win7 on an unformatted drive, it defaults to a two-partition setup, the first being a boot partition, the second being the OS partition.  This setup has been known to present problems in some cases with multi-booting.  So, instead, you should format an NTFS partition on your drive (30GB or so) to hold Win7.  Then, when you boot from the DVD to install Win7, point it to the NTFS partition and have it reformat it -- this is important.

Of course, after you install Win7, you'll have to reinstall GRUB.  But when you do that, make sure it does NOT get installed to all the partitions.  IF it gets installed to the Win7 partition, that will prevent Win7 from booting.

And finally, I would create a single, large, NTFS data partition for sharing data, rather than automounting the Win7 OS partition.

---

### Post by capitalfear on 2010-08-03
dude that just made my head spin....wow okay, what order should i do it in? from the way you said it win should be first?

---

### Post by uRock on 2010-08-03
If it helps, here is a screenshot of my setup. As you can see Windows has the first partition.

uRock

---

### Post by WorMzy on 2010-08-03
Windows doesn't need to be in the first partition though, it doesn't even need to be in a primary partition.

Here's a screenshot of my partitions:
[URL="http://img217.imageshack.us/img217/4563/20100803191224777x523sc.png"]
[IMG]http://img217.imageshack.us/img217/4563/20100803191224777x523sc.th.png[/IMG][/URL]

I have Ubuntu 9.10 first, Ubuntu 10.04 second, Windows Vista third, then an extended partition with, swap, XP home, Debian 5.10, Arch 64-bit, and Arch 32-bit.

---

### Post by capitalfear on 2010-08-03
thanks that helps big time
so let me get this straight. i use gparted...after i install whatever os i start on? then just do any of them afterwards?

---

### Post by uRock on 2010-08-03
> **WorMzy said:**
> <snip>
Do you ever sit there staring at the grub menu debating which choice to make?;)

---

### Post by uRock on 2010-08-03
> **capitalfear said:**
> thanks that helps big time
so let me get this straight. i use gparted...after i install whatever os i start on? then just do any of them afterwards?
It is best to install Windows first, in any position, so that it can do its MBR thing, then you can install Linux with grub.

---

### Post by WorMzy on 2010-08-03
You can use a LiveCD before you install any OS' to divide your disk into however many partitions you want; but Windows should have it's own partitioner which you can use during it's installation process if you'd prefer to use that. You'll need to pay attention during each OS installation, making sure that you install each one to it's own dedicated partition, rather than over the top of an existing OS.

Just bear in mind that you can (usually) only have four primary partitions on any disk, so if you plan on making more than four partitions, make sure that you make the fourth partition an extended partition, and have it stretch the full width of the disk, so that you can continue to make partitions inside of it.

You only need one swap partition between all your Linux partitions.

[QUOTE="uRock"]Do you ever sit there staring at the grub menu debating which choice to make? ;)[/QUOTE]

Occasionally. :P

---

### Post by realzippy on 2010-08-03
> **uRock said:**
> Do you ever sit there staring at the grub menu debating which choice to make?;)

Yes.And I hate it if I have to take the last choice...

---

