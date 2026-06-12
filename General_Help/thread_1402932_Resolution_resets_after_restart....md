---
title: "Resolution resets after restart..."
date: 2010-02-09
forum: General Help
---

### Post by Powerman2442 on 2010-02-09
Hopefully I get help with my question, as my past few haven't got a single reply in weeks. :(

So I just did a clean install from Ubuntu 8.04 LTS to Ubuntu 9.10. I went to System -> Administration -> Hardware Drivers to enable any drivers (mainly for my graphics card so I could run higher resolutions). Had two driver, one for my wireless network interface card and one for my graphics card (NVIDIA Geforce FX 5200). I enabled the drivers restarted and went to System -> Administration -> NVIDIA X Server Settings. The resolution was set to "Auto", which is 1280 x 1024 (max.) on my old CRT. 

I've ran that resolution for a day now and it isn't as snappy as I'd like it to be (or as the exact same resolution was on 8.04). So I reverted back to 1024 x 768. Everything seems to be running as I'd hope under the lower resolution. The only problem I am running into now is when I restart NVIDIA X Server Settings changes back to "Auto" and automatically switches to 1280 x 1024. I've clicked "Save X Configuration File" thinking that might help retain the resolution I want after startup, but it just says "Failed to parse existing X config file '/etc/x11/xorg.confg'!"

How do I get my resolution to stay at 1024 x 768 after a restart?

Thanks

---

### Post by Easy Limits on 2010-02-09
I have had the same issue with my video card (GeForce 7300 GS).  I found a solution though.  

Here it is:  Go to System > Preferences > Display.  A window will pop up asking you if you want to use the graphics driver vendor tool instead.  Click on No.  Another window will pop up and you will be able to set your resolution with it and your resolution will stick after you re-boot.

---

### Post by wojox on 2010-02-09
Open a terminal and run:

```
sudo nvidia-xconfig
```

Then:

```
gksudo nvidia-settings
```

This will make it stick.

---

### Post by Powerman2442 on 2010-02-09
Easy Limits - If wojox method doesn't work I will try yours.

wojox - I have a lot going on currently, but I've entered the two commands in terminal that you've provided. I'll restart my computer later tonight and edit my comment to let you know if it worked or not.

Thanks to both of you. :)

wojox, I entered the two commands you provided and the resolution still reset after a restart. I also tried Easy Limits way and the resolution is staying after a restart. The only thing I noticed about Easy Limits way is that my refresh rate is 57 Hz when it was 70+ while using the NVIDIA X Server Settings.

---

