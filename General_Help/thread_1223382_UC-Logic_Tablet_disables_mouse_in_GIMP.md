---
title: "UC-Logic Tablet disables mouse in GIMP"
date: 2009-07-26
forum: General Help
---

### Post by kmolnar on 2009-07-26
Hi all!
I'm using a UC-Logic tablet (branded: WP8060, lsusb reports "Genius MousePen") with The GIMP. I have found that once The GIMP switches to extended input (when I use the tablet) it stops responding to the mouse.

The mouse still works for menus and such, as expected, but doesn't do anything in the editor window.

There is another thread going related to Wacom tablets exhibiting the same behavior, but I'm not sure if the two are related. It seems the Wacom tablets export a whole bunch more Extended Input devices than my tablet does.

I've been told disabling the mouse in the extended input manager will solve it, but I have tried this with no success. The tablet works fine, but it's kind of useless to me if I can't also use the mouse for fine-grained pixel work.

Thanks for your time! I hope we can solve this! =)

---

### Post by Favux on 2009-07-26
Hi kmolnar,

In Gimp's "Configure Extended Input Devices" which mode do you have the stylus and mouse set to?  Screen or disabled or window?  Try playing with those settings.

---

### Post by dubbs on 2011-05-01
i think i found the solution! wp8060 worked great before 8.10 or so then didnt work with later ubuntu releases 
im running 11.04 and didnt work with that either, BUT, i reinstalled 11.04 a second time, this time with wp8060 attached to the computer. when once installed worked but no mouse buttons worked, so i had to disconnect and reset then once os was on reattached wp8060 and worked perfectly. maybe works with earlier ver. too

steps 
1 install ubuntu with wp8060 attached 

2 when up and running make sure you have movement then 

3 disconnect and reset 

4 once ubuntu is running plug back in, and should work 

working for me would like to know if we finally found solution so please reply.

---

