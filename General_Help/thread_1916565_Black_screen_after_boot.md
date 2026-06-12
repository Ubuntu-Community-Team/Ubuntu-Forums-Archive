---
title: "Black screen after boot"
date: 2012-01-28
forum: General Help
---

### Post by xenon53 on 2012-01-28
Hi guys i have the laptop Asus k53ta.After the OS boots,the gpu sends the graphics to the HDMI port and not to the display of the laptop and thats why the laptops screen is black.I can see the graphics if i connect the laptop to an external monitor via HDMI cable.
Does anyone know how can i change the graphics output and how to make the laptop display the default display?:confused:

---

### Post by akvik on 2012-01-31
Hi,

I have the exact same problem with the new kernel (3.0.0-15-generic) on latest oneric, HP Elitebook 2540p. If I don't have the laptop connected to an external display, it goes black (however with background light on). Have tried all kinds of tweaks, such as FN + F4 to reroute the signal to my built-in screen.

My work-around is to boot the previous kernel (3.0.0-14-generic) by pressing ESC during grub, selecting "Previous Linux kernels" and choosing 
3.0.0-14-generic.

This also has a side-problem once booted with the 3.0.0-15-generic kernel, I can't seem to get both displays to work, only the external one. Meaning that it's the same problem then as when booting without the display.

---

### Post by akvik on 2012-02-13
Hi,

The problem described in post 2 have now been solved with the upgrade to the 3.0.0-16-generic kernel. Everything works as expected.

---

### Post by sandy8925 on 2012-02-14
i have the same laptop, there was a bug in the Linux 3.0 kernel. this has been fixed in Linux 3.2, and it looks like the Ubuntu devs have backported that fix to 3.0.0-16. if you're still not able to get it to work then try compiling kernel 3.2.

---

