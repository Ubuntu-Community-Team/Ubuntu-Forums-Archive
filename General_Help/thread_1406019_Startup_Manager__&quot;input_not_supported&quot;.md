---
title: "Startup Manager  &quot;input not supported&quot;"
date: 2010-02-13
forum: General Help
---

### Post by bigsmitty64 on 2010-02-13
Hey everyone,
I downloaded and installed "Startup manager" from the symantic package manager, allowing me to change my boot order in a dual setup. Works great, but I HAD to mess with it, and I changed some settings in the program. Now When I boot, I can't see grub! its says "input not supported!" The settings I changed were, 
> 1) Changed the startup managers rez to 1600x900
2) Changed the theme of the startup manager
Now I can't get to my Ubuntu desktop.What do I do ?

Any help is greatly appreciated,thanks in advance,
Smitty

---

### Post by tom4everitt on 2010-02-13
Here you can read about how grub2 works, and what your /boot/grub/grub.cfg file should look like:
[http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html) 

To fix your grub you need to boot from a live cd and make that file correct. (If you're lucky startup manager might have created a grub.cfg backup in the same folder.)

If you need help you could post the contents of your /boot/grub/grub.cfg file here, and I or someone else can suggest changes.

---

### Post by bigsmitty64 on 2010-02-13
Thanks a lot Tom,
I fixed it by letting it boot to the grub and when it said, input not supported, I just hit the up button a few times (even though I couldn't see anything) that must have still brought the cursor to the top because it booted to my Ubuntu that time! Then I could fix it from the Startup Managers GUI.  But I will remember this advice for the future,thanks again,
Smitty.

---

