---
title: "Run alongside Windows (how to uninstall)"
date: 2011-10-07
forum: General Help
---

### Post by BruceyBonus on 2011-10-07
I've recently installed the latest version of Ubuntu on my laptop as a dual-boot with Windows (I've been using it on my desktop for many years).

I pressed an option like "run alongside Windows".  I expected this to use the unpartitioned space.  Instead, it seems to have installed on my NTFS partition.

What I'd like to do is remove this copy, then reinstall into the free space.

Does anyone know the best way of completely removing Ubuntu from the NTFS partition?

---

### Post by coffeecat on 2011-10-07
It sounds as though you may have created a wubi installation although, to be honest, I wasn't aware that you could create a wubi from the live CD installer. Or did you download a file called wubi.exe which you ran in Windows? A wubi installation is easily removed, but before you do anything, in case you have some other configuration, let's see what your system and partition layout is like. Boot into Ubuntu and post the output of these terminal commands:

```
sudo fdisk -lu
mount
cat /etc/fstab
```

You can highlight the output with the mouse, copy it with a right-click, and then paste it into your post. Please enclose the outputs between [noparse]```
 and 
```[/noparse] tags for clarity.

---

### Post by BruceyBonus on 2011-10-07
Installed straight from the Live CD - didn't use Wubi.

I've not got the laptop with me today, so I'll pop those commands into the terminal first thing tomorrow morning,

---

### Post by bcbc on 2011-10-07
Control panel, add/remove programs, look for and double click on "Ubuntu". (That's if you installed while windows was running, even if you used the CD).

But since you said you didn't just do what coffeecat said.

---

### Post by Mark Phelps on 2011-10-08
If you BOOTED from the CD, you did a normal install -- and since that can't install to an NTFS partition, if you did use THAT partition, you reformatted it and overwrote it with Ubuntu. Meaning, in that case, Win7 is GONE.

So, if that's the case, the more pressing problem may be getting Win7 back.

---

