---
title: "Way too many entries at the boot screen how do I remove?"
date: 2010-01-28
forum: General Help
---

### Post by axima on 2010-01-28
Here is the boot screen

[IMG]http://img638.imageshack.us/img638/3038/img0271k.jpg[/IMG]

What can I do to get rid of some entries?

9.10 64bit user here

---

### Post by llawwehttam on 2010-01-28
Go to Synaptic Package Manager and search for *linux-image*. This will list the installed kernels. Uninstall all but the latest two ( you need to keep one before the latest in case you have problems) then run
```
sudo update-grub
```That should work.

Also to find out your latest kernel ( the one you DO NOT want to remove) open terminal and type ```
uname -r
```

---

### Post by drs305 on 2010-01-28
The simplest thing is to remove some of the older kernels. Here is a link. Near the bottom is a discussion of how to remove them:
[http://ubuntuforums.org/showthread.php?t=818177]("http://ubuntuforums.org/showthread.php?t=818177")

Read the entire section, as Ubuntu-Tweak is one of the easiest but comes later in the section.

---

### Post by presence1960 on 2010-01-28
The best way to get rid of kernels you don't want is to mark them for Complete Removal in Synatic Package Manager. You should leave two in case the most recent kernel borks- then you can boot into the other kernel.

Boot into the 9.10 on sda5 and mark for Complete removal:

linux-headers-2.6.31-14
linux-headers-2.6.31-15
linux-image-2.6.31-15
linux-image-2.6.31-14

Also if there are entries with the above followed by -generic remove them also.

Then boot into which ever 9.10 controls GRUB and open a terminal and run ```
sudo update-grub
```
The GRUB entries for the kernels you removed will be gone when the command updates grub.cfg. Next time you boot the entries will be gone.

P.S sorry I didn't see drs305 posted- must have done so while I was typing. That will work also.

---

### Post by axima on 2010-01-28
> **llawwehttam said:**
> Go to Synaptic Package Manager and search for *linux-image*. This will list the installed kernels. Uninstall all but the latest two ( you need to keep one before the latest in case you have problems) then run
```
sudo update-grub
```That should work.

Also to find out your latest kernel ( the one you DO NOT want to remove) open terminal and type ```
uname -r
```

Works! Thanks!

Problem is solved!

---

