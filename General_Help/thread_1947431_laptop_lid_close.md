---
title: "laptop lid close"
date: 2012-03-26
forum: General Help
---

### Post by ffmurray on 2012-03-26
Im running 10.04lts on my acer 5250.  The screen has several cracks on it that make it unusable.  I hooked it up to a monitor and am using it as a desktop.  I want to be able to close the laptop lid and have nothing happen, so I ran gconf-editor and opened up the power settings and set ac_lid and battery_lid both to nothing,  and it changed nothing.  on both ac and battery power the computer suspends as soon as the lid is closed.  I had done this once before on the same computer also running 10.04lts but i tried to upgrade it to 11.10 but could not get it to work, i did a clean install of 10.04 lts and now i cant get it to do nothing when the lid is closed.

---

### Post by papibe on 2012-03-26
Hi ffmurray.

I have a laptop with a similar problem.

A few ideas:
[LIST]
[*]Look for extra modules made specifically for your brand and model that can add better access to your laptop's power settings (check for ppas on Launchpad for example).
[*]Check the BIOS is case there are hardware power settings there too.
[*]If you are dual booting with Windows, you can set the power settings there, and almost for sure they will apply for Ubuntu too.
[/LIST]
Just some thoughts.
Regards.

---

### Post by ffmurray on 2012-04-05
I ran gconfig editor again and changed the settings back to default then set lid_ac and lid_battery to nothing, i did this on three consecutive days with no changes in how the laptop lid settings worked.  on the fourth day i did it one more time and it worked, i didnt do anything different and have had not run any updates.  i dont know how it worked that time or why but it did

---

