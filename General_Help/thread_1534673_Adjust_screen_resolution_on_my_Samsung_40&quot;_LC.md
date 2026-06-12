---
title: "Adjust screen resolution on my Samsung 40&quot; LCD"
date: 2010-07-19
forum: General Help
---

### Post by Xonnie316 on 2010-07-19
Hey Ubuntu users,

I'm a complete Ubuntu/Linux n00b. So please bare with me here. I have an HTPC mini computer, in which I've just installed Ubuntu 10.4 Lucid Lynx, and I tried all screen resolutions I could possibly use through the settings. And the top, bottom, left & right hand sides are out of the resolution.

So for example the top and bottom taskbars are out of the screen. I'll be posting a photo later on today to show you people exactly what I mean.

Is there a way I could adjust this ??

So that I can have Ubuntu's screen would fit all inside my LCD screen ?

Would really appreciate some help :)

The HTPC runs an nVidia graphics card.

---

### Post by cariboo on 2010-07-19
How are you connecting to the TV? I have a 32" Samsung, I use the vga connector and get the tv's native resolution of 1360X768. For Auto-setting the picture, I go to Setup->PC on the TV menu.

**Note:** this setting only works when the computer is connected and turned on.

---

### Post by LeeDaugherty on 2010-07-19
This is called overscan and is a common-problem due to the difference between televisions and computer monitors.  You are using nVidia video card and since you are doing a HTPC, I would assume you have installed nVidia's proprietary drivers to maximize your video performance?  If so, the overscan can easily be correct via the nVidia X Server Configuration Utility found under System -> Administration.  While this isn't the perfect solution (perfect solution will require a decent amount of work) it is by far the easiest and works just fine.

---

### Post by Xonnie316 on 2010-07-19
>  How are you connecting to the TV? I have a 32" Samsung, I use the vga connector and get the tv's native resolution of 1360X768. For Auto-setting the picture, I go to Setup->PC on the TV menu.

Note: this setting only works when the computer is connected and turned on.


I have my HTPC connected to the LCD using an HDMI Cable.

> This is called overscan and is a common-problem due to the difference between televisions and computer monitors. You are using nVidia video card and since you are doing a HTPC, I would assume you have installed nVidia's proprietary drivers to maximize your video performance? If so, the overscan can easily be correct via the nVidia X Server Configuration Utility found under System -> Administration. While this isn't the perfect solution (perfect solution will require a decent amount of work) it is by far the easiest and works just fine.

Its actually picked up the nVidia drivers and I've updated it.

Thanks very much, I'll give it a shot later on today. Sounds like it should do the trick.

---

