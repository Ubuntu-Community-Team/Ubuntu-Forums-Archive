---
title: "Kernels Galore"
date: 2011-03-25
forum: General Help
---

### Post by fallofshadows on 2011-03-25
So, I've been trying to use Ubuntu tweak to clean up the excess kernels on my boot screen. However, when I'm in Ubuntu tweak, the version of the kernel is 2.6.35-28 generic. The most recent kernel on my boot screen, however, is 2.6.35-25. What's up with that?

Thanks

---

### Post by lithopsian on 2011-03-25
Beats me.  That's what happens when you use a black box to do the work for you.  If the black box is wrong, then you're screwed.

Have a look in your /boot and see what kernels you actually have.

---

### Post by ajgreeny on 2011-03-25
Use the command ```
grep menuentry /boot/grub/grub.cfg
``` to see what you really have in your grub menu, just in case something has gone wrong with the grub display.

It is rather baffling and I can not imagine what is going on, but you can find out which kernel you are running at the moment with ```
uname -a
```

---

### Post by fallofshadows on 2011-03-26
Well this is odd. I do indeed have the -28 kernel on my machine, but my grub screen doesn't show it. Because of this, I'm running the -25 kernel right now.

Is there a way to update/fix my grub screen then? That seems to be the problem.

---

### Post by cipherboy_loc on 2011-03-26
Try running:

```

sudo update-grub2

```


Cipherboy

---

### Post by fallofshadows on 2011-03-27
I ran that, and the console acknowledged that there's a -28 version of the kernel, but my grub still won't show it :(

I'm using the fancy GUI version of the grub, ie. not the standard one that appears after you install ubuntu. Would this have something to do with it?


-------
EDIT: 

Heyo! I found, via the grub information page on these forums, a GUI program that edits what appears in your grub menu. Upon installing this program (Grub Customizer) it informed me that it detected a BURG, and wanted to know if I wanted to edit that instead. I said yes, unchecked the kernels I don't want to use, and viola! My boot menu is now up to date, and much much shorter. 

Thanks for all the help you guys provided! I guess I should have remembered that I'm using BURG, not GRUB2 as most people :/

---

### Post by Legeril on 2011-03-27
Old kernals can take up a lot of space if you let them pile up use this command

```
dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get -y purge
```

And that will clear all your un-used kernals, you can gain a lot of memory back if you have a big pile of kernals.

---

### Post by fallofshadows on 2011-03-27
Eh, I'd rather use ubuntu tweak and have a GUI to work with when it involves something as complex as kernels. Thanks anyways though!

---

