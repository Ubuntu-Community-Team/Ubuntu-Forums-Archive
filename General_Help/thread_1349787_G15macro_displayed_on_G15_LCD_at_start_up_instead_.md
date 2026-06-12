---
title: "G15macro displayed on G15 LCD at start up instead of clock"
date: 2009-12-08
forum: General Help
---

### Post by PlugInPrius on 2009-12-08
I've followed the guides on installing the G15macro and placed it in the preferences>startup. When the computer starts I have G15macro on the LCD by default and wont switch to the clock until I press the button on the keyboard to switch it.

I was wondering how I would fix it so the clock is displayed at boot and not the G15macro logo.

I've been looking into different ways to run start up applications and found something that may work.

I was wondering if I could make a script in the init.d directory and have it run before the G15daemon?

I have not tried this yet because I have no clue on how to make a script for this to work.

Has anyone had this problem and fixed it?

---

### Post by PlugInPrius on 2009-12-09
Well I tried making a script to start in the init.d but the g15daemon must be running before you start the g15macro.

I'm still looking a solution to get the clock to automatically display after the g15macro has loaded.

---

