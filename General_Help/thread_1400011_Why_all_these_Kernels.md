---
title: "Why all these Kernels"
date: 2010-02-06
forum: General Help
---

### Post by Thomas Garman on 2010-02-06
I have been trying to get my Pinnacle PCTV HD usb stick to work and so I followed the instructions here:

[http://www.linuxtv.org/wiki/index.php/Pinnacle_PCTV_HD_Pro_Stick_%28801e%29#Making_it_Work](http://www.linuxtv.org/wiki/index.php/Pinnacle_PCTV_HD_Pro_Stick_%28801e%29#Making_it_Work)

which did not work for me BUT in the course of installing everything that has to be installed using those instructions, a couple more kernels have been added to my GRUB.  I also installed the entire Ubuntu Studio Video package to try to get everything into my system that would be needed to play tv on my computer through my usb stick.  The tv has never worked BUT now I am showing 5 kernels in my Grub menu.

MY QUESTION IS THIS:  what are all of these kernels?  I have never booted into anything other than the one listed as 2.6.31-18, which is my Jaunty 9.04 (with updates) installation.

I know that I can go into Synaptic and delete the kernels and nothing really happens, because I did that when I was running Karmic 9.10 (which I stopped using because I could never get the audio to work properly and LMMS never worked at all).

SO: why does anybody need all of these kernels and in particular since the video package works just fine in every way using the normal 9.04 kernel why would I ever boot in the rt kernel?

THAT IS MY QUESTION:  why would I ever boot into any of the other kernels.  Is there some benefit to booting into the rt kernel that I am not aware of?

---

### Post by Bachstelze on 2010-02-06
> **Thomas Garman said:**
> 
THAT IS MY QUESTION:  why would I ever boot into any of the other kernels.  Is there some benefit to booting into the rt kernel that I am not aware of?

"rt" in the rt kernel means "real time", which basically means that the kernel processes data as soon as it gets it. Ubuntu Studio installs it because some multimedia production applications need it. If your system is working fine without it, then you absolutely don't need it.

To remove a kernel from your GRUB menu, uninstall the corresponding [font=monospace]linux-image[/font] package.

---

### Post by Teunis on 2010-02-06
You should really use the latest kernel, the one on the top of the list.
The update system of Ubuntu takes a safe route by not uninstalling a previous kernel, in case of trouble with the new one you have the chance to select the old one.

Once convinced the latest works you can simply remove the previous one(s) through the package manager.

---

### Post by ssulaco on 2010-02-06
Yes,keep the two most current kernels and remove the rest,you can remove unwanted kernel images and headers via the terminal
```
sudo apt-get remove --purge 2.6.xx-xx-*
```
where xx is the kernel you want to remove,

---

