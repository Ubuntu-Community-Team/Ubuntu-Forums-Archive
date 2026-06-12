---
title: "Problem with nvidia driver in kubuntu"
date: 2009-09-17
forum: General Help
---

### Post by bento024 on 2009-09-17
Hi,

So I had my laptop setup to use Twinview with an external monitor. I was using gnome, but I switched to KDE because it seemed to have more support and customization for dual monitors. I setup a boot script so that I could choose between two different xorg.conf files depending on whether I had my laptop docked with the external display or not. Everything seems to be working fine with that.

When I undocked my laptop and booted up using the appropriate xorg.conf, everything went fine up until I logged in. When I would log into Kubuntu, it would come up with no desktop. The cursor and my windows were still there, but no background, no panels, nothing. It's important to note that everything from compiz was still working at this point. Also, booting into gnome gave me no problems whatsoever. Everything is exactly like it was before.

After a lot of searching around, I tried changing the driver in xorg.conf from nvidia to vesa. This fixed the problem with the black screen, but, of course, compiz doesn't work this way. I really want to get that working, but I can't figure out what's going wrong when I use the nvidia driver. I've tried uninstalling and reinstalling the drivers, but no luck. I can't be sure I did that correctly, though.

My xorg.conf is about as basic as you can get. I ran dpkg-reconfigure xorg-xconfig and then used nvidia-xconfig to set it up for nvidia. After that, the only change I made was to change the driver to vesa.

Any help would be much appreciated.

Thanks

---

### Post by bento024 on 2009-10-09
bump

---

