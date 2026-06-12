---
title: "Power settings??"
date: 2010-08-26
forum: General Help
---

### Post by chris0108 on 2010-08-26
Hi there,
    This might be a really simple question but when my laptop is running of the battery the screen goes fairly dark, i dont like this, iv changed the power settings to try and stop it (unticking the reduce backlight) but it doest do anything. Iv looked around and done a google search but just dont seam to be able to find anything, anyone know how this can be done?

Many thanks Chris

---

### Post by afrowildo on 2010-08-26
Have you unticked the 'Dim display when idle' option beneath the 'Reduce backlight' option? Also, does your laptop have brightness control keys on it's keyboard? On my laptop, I can control the brightness using <Fn+Right Cursor> and <Fn+Left Cursor> to brighten or dim the display.

---

### Post by chris0108 on 2010-08-26
I only have the "reduce brighness" one on mine, im running 9.10. Yes iv got the brightness control on my laptop (explained why i only had a black screen when i put ubuntu on LOL) only trouble doing it that way is that i have to turn it back down when it back on mains power.

---

### Post by afrowildo on 2010-08-26
Does this site help you out at all?

[http://www.ossramblings.com/set_battery_backlight_dim_amount](http://www.ossramblings.com/set_battery_backlight_dim_amount)

BTW, the configuration editor may not be visible in your applications list, in which case you'll have to open the menu editor (**System** -> **Preferences** -> **Main Menu**), select **System Tools** and enable it from there.

---

### Post by chris0108 on 2010-08-26
Thank you for that think its sorted it out just going to reboot and make sure.

Chris :D

---

### Post by chris0108 on 2010-08-26
Well changed everything and no it still does dark when the power is unplugged, why is this so hard to sort out??

---

### Post by afrowildo on 2010-08-26
I'm able to replicate your problem on my own computer. From experience, I've found Linux power management to be pretty sub par, especially when compared to what's on offer in Windows 7 and Mac OS 10.6. Unfortunately, I don't think there is a solution to this short of adding the feature directly into Ubuntu.

Ubuntu has (in case you didn't know) a project in place called *One Hundred Papercuts*, whereby a hundred usability bugs (as opposed to technical bugs) as fixed every release cycle (that's every six months). I've submitted this as a papercut, so why don't you [head on over to Launchpad]("https://bugs.launchpad.net/hundredpapercuts/+bug/624928") and vote it up, thus helping bring it to the devs attention.

---

