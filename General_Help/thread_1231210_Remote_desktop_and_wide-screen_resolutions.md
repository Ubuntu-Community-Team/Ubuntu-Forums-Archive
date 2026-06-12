---
title: "Remote desktop and wide-screen resolutions"
date: 2009-08-04
forum: General Help
---

### Post by jackleather on 2009-08-04
Hi, i have ubuntu working nicely after defecting from fedora 11 - thanks to all the effort thats gone into it.

I am running a **headless **machine and am using the built in remote desktop (rather than installing vncserver) to connect. 

I have modified xorg.conf several times with varying degrees of success. The most encouraging change was to the HorizSync and VertRrefesh entries. I now have a remote desktop of 1024x768, which is much better than 640x480!

However the machine i remote desktop from (MacBook Pro) has a res of 1280x720. in other words i get scroll bars and must use them to view the top and bottom panels of the gnome desktop.

So how do i add a resolution of say 1152x700 (or whatever fits) to xorg.conf which isnt rejected as;
Not using built-in mode "1600x1200" (no mode of this name)
or
Not using built-in mode "640x400" (hsync out of range)

Xorg.0.log reports that its using VESA - which is fine as i dont need any acceleration etc.

Please Help!

---

