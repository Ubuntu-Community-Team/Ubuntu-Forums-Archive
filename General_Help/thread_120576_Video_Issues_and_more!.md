---
title: "Video Issues and more!"
date: 2006-01-22
forum: General Help
---

### Post by cityofdoors on 2006-01-22
Hey,

I just installed Kubuntu on a newly built computer. I was getting these weird blank fritzy boxes for a while. Then I stopped getting any picture at all, so I switched from my video card (xfx Geforce 6200) to my built in video chip (Integrated ATI* Radeon* X300 based graphics), but now, oddly enough, I can see things again, but for some reason, the computer doesnt go directly to the graphic interface and goes to the command line instead. The screen does blink black twice during the loading process, but that's it.

I'm a complete nube at Linux, so please be very descriptive. ;) 

Thanks a lot!

---

### Post by pelle.k on 2006-01-23
The two cards might be driving it mad?
Log in, and do this "sudo dpkg-reconfigure xserver-xorg"

Just press return/enter for default answer, but keep an eye on what is asked. You want to choose your graphics card and choose "nv" as you xserver. "vesa" might work too but it's not as fun as "nv".
Can you deactivate your built in card in BIOS?

---

