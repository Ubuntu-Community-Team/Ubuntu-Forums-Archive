---
title: "FATAL: module ext3 not found"
date: 2006-02-20
forum: General Help
---

### Post by nrwilk on 2006-02-20
I recently compiled the latest kernel, 2.6.15.4, and, I had a problem with the startup splash not being displayed at all.  I learned that this is normal for kernels >= 2.6.15.  One of the things I had wanted to do was to disable the annoying graphical splash that displayed anyway, so I removed the graphical splash and I'm happy with the verbose terminal which now displays.

But, just after it says "uncompressing the kernel" (or something equivalent), I get a line which says simply, "FATAL: module ext3 not found."

After that, the boot process is normal and everything works correctly.  Should I be worried?  Is this normal?  Should I try to fix something.

I am sure that I compiled ext3 support directly into the kernel.  Does it have to do with that?

---

### Post by dcstar on 2006-02-20
[QUOTE=nrwilk]
......
I am sure that I compiled ext3 support directly into the kernel.  Does it have to do with that?[/QUOTE]
Probably, try:

sudo modprobe -r ext3

to remove it from your module loading list (hopefully this won't break your system.........)

---

### Post by slux on 2006-02-20
modprobe -r just attempts to unload a module from the running kernel as far as I know.

Your error message does  relate to you compiling ext3 support directly into the kernel. Somewhere early in the boot process (initrd script?) the ext3 module is requested to be loaded but as there isn't a module for that in your kernel, the loading fails. The problem is entirely cosmetic and is no cause for any real concern. Unfortunately I don't have any advice on what exactly causes the failed loading attempt so I can't help you with that.

---

### Post by nrwilk on 2006-02-20
[QUOTE=slux]The problem is entirely cosmetic and is no cause for any real concern.[/QUOTE]
Well that's good.

[QUOTE=slux]Unfortunately I don't have any advice on what exactly causes the failed loading attempt so I can't help you with that.[/QUOTE]
Dang.  That would have been a nice learning experience.

Thanks, slux!

---

### Post by zappa86 on 2006-02-21
You may have put yourself in a catch-22. Your ext3 module is on your harddrive that has the ext3 filesystem on it. and in order to get the module you must read it from your harddrive, but to do that you need the module. When you compiled your kernel did you make the inital ramdisk. Are you using the debian method of compiling a kernel the make-kpkg or the olderschool method of make && make install and such? You could recompile your kernel with EXT3 built in instead of a module. this may help, or you could figure out how to do the initrd. Try using the debian method of making a custom kernel. I say the easiest is just to compile ext3 into the kernel and forget it as a module.

---

### Post by engla on 2006-02-21
I have the same issue and the same cause [basically]

I figured it was safest to not do anything about it -- if I reboot to an older kernel I need the ext3 module to load.

---

