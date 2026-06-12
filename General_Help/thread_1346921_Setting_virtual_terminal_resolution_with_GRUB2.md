---
title: "Setting virtual terminal resolution with GRUB2"
date: 2009-12-05
forum: General Help
---

### Post by pbrane on 2009-12-05
I have '**vga=791**' added to **GRUB_CMDLINE_LINUX_DEFAULT** in /etc/default/grub. This seems to work to set the VT resolution however I get that warning during boot that 'vga=791 is deprecated...'. While this still works, some day it may not.

I have also set **GRUB_GFXMODE=1440x900x32** in the same file, grub2 sets that correctly for the boot screen but does not set the VT resolution this way. 

My question, is there a better way to set the VT resolution? A way that is not deprecated and may go away in future releases. I can't seem to find anything that works in the grub2 documentation or searching this forum or google.

---

### Post by wilberfan on 2009-12-13
I've just spent close to an hour looking for a solution to this as well!  No luck so far....

---

### Post by UrbenLegend on 2009-12-17
I am having the same problem as well. I have tried setting gfxpayload=true in GRUB_CMDLINE_LINUX, but it does diddly squat. This is a really annoying problem and no one seems to have a correct solution.

---

### Post by pbrane on 2009-12-17
I have tried gfxpayload as well. I looked at suggestions in other forums and even asked on #grub IRC. It may be a problem with the framebuffer. When I load vesafb (after commenting the blacklist line) I get no VT at all. But gfxpayload is supposed to be what we need. I added GFX_PAYLOAD=<various resolutions> to /etc/default/grub and edited /etc/grub.d/00_header but nothing has worked.

I'm not sure adding gfxpayload=true to the linux command line is correct though. I found forums that say to add this to /etc/default/grub and then edit /etc/grub.d/00_header to make this work. One gave the framebuffer workaround, but none of this worked.

For now I use vga=791 in my linux command line and just ignore the grub warning. It would be nice if a solution is found.

I did note that this apparently does work in some distros. At least that is what I'm seeing in other forums.

---

### Post by UrbenLegend on 2009-12-17
I too used the vga option, but I don't think the kernel supports it with the video backend that its using. Whenever I set vga=369, which is 1680x1050, and attempt to switch to a virtual console, the screen flickers and then the resolution falls back to the nearest 4:3 resolution. What is the framebuffer workaround?

---

