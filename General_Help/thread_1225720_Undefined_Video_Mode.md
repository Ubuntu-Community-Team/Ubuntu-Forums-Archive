---
title: "Undefined Video Mode"
date: 2009-07-28
forum: General Help
---

### Post by kornfan71 on 2009-07-28
Hello all,
I'm having this issue with all of my Linux installations, so I'll start with the one I use most. When I boot into Ubuntu 9.04, it says that video mode "31b" is undefined. I have the kernel command "vga=795" in my GRUB menu.lst, since it's the best resolution my lowly old CRT can handle (upgrade soon, hopefully  ;-)).
I have a Sapphire Radeon HD 3870 512 MB. I downloaded the driver that ATI supplies on their website, that also contains Catalyst Control Center. ---2D Driver Version 8.62.4; CCC Version 2.7---

When it fails to find the video mode, I am able to select video mode "324" from the list, and it works just fine. So, what can I do to not put in "324" every time I boot to Ubuntu, while still maintaining my 1280x1024 console? (i.e. How would I be able to use the 324 in GRUB, if at all?)

Thanks in advance.

---

### Post by plucky on 2009-07-29
> When I boot into Ubuntu 9.04, it says that video mode "31b" is undefined

Remember when the system is booting,your video card driver is not loaded initially,so your video card needs to use a lower resolution.

Try altering your resolution using the vga=XXX according to this table to a lower colour depth and then lower resolution until the undefined video mode goes away.

```
 
Screen  640x480  800x600 1024x768 1280x1024 1600x1200
Colors 					
256 	  769 	   771 	    773     775 	796
32,768 	  784 	   787 	    790     793 	797
65,536 	  785 	   788 	    791     794 	798
16.8M 	  786 	   789 	    792     795 	799

```

and then running the command from a terminal ```
sudo update-initramfs -u -k all
``` before rebooting to test if it works.


Good Luck

---

### Post by kornfan71 on 2009-07-29
OK, a step down in color seems to have fixed it for some reason. I was just questioning it since my old card could run 1280x1024 w/ 24 bit color, and now the new card can only run 1280x1024 w/ 16 bit color on the console. Whatever....

Thanks!

---

