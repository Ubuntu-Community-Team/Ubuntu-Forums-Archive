---
title: "Nvidia Drivers for Dell Inspiron 5150"
date: 2010-04-23
forum: General Help
---

### Post by Mic[RSA] on 2010-04-23
In a previous thread I stated that I had updated my old dell's nvidia drivers only to receive a blank screen (of deadly doom) in return. Now however I would like to try and install them again, but this time not through the hardware drivers app. Where do I do this and which drivers should I get. My google searches has failed me.

Sorry for being such a newb, still getting a hang of this OS. Loving it so far :D

---

### Post by cascade9 on 2010-04-23
What drivers you should get will depend on what video card you have, so console, then-

[FONT=monospace]lspci

[/FONT]That should give you lots of info, but you are only looking for the VGA controller- 
[FONT=monospace]
[/FONT]```
[FONT=monospace]01:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600 GT] (rev a1)[/FONT]
```

What model card you have will vary the actual nvidia drivers you need. 

Then go to the nvidia site- 

[http://www.nvidia.com/Download/index5.aspx?lang=en-us](http://www.nvidia.com/Download/index5.aspx?lang=en-us)

Go though the selection process, d/l the right driver, then start tapping away at a console again, dircetions here- 

[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

Sorry that the manual driver install page is a bit complicatied, I would link you to the (better IMO) debian manual install directions but I'm not 100% sure that it works with ubuntu.

---

### Post by Mic[RSA] on 2010-04-23
Well here is my gfx card details.
```
01:00.0 VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go5200 64M] (rev a1)
```The drivers I want to install does not show the FX go5200 but they do show many other FX 5200... should it still work?

---

### Post by Mic[RSA] on 2010-04-23
I downloaded a .run file for the driver I think will work and the nvidia instructions says to type: sh  NVIDIA-Linux-x86-173.14.25.pkg1.run. I'm guessing that is in the terminal. should it work?

[http://www.nvidia.co.uk/object/linux_display_ia32_173.14.25_uk.html](http://www.nvidia.co.uk/object/linux_display_ia32_173.14.25_uk.html) here is the link to look at the install guide.

---

### Post by klemes on 2010-04-23
Yes exactly in the terminal with no X running.
For this purpose type first (as root) /etc/init.d/gdm stop
and then run sh /path-where_it's_saved/NVIDIA[.....].run

---

### Post by cascade9 on 2010-04-24
> **'Mic[RSA] said:**
> Well here is my gfx card details.
```
01:00.0 VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go5200 64M] (rev a1)
```The drivers I want to install does not show the FX go5200 but they do show many other FX 5200... should it still work?

Damn, nVidia doesnt have offical support for the FX5200Go? Unimpressed. 

The 173.xx drivers that work with the other FX cards should work though. 


> **'Mic[RSA] said:**
> I downloaded a .run file for the driver I think will work and the nvidia instructions says to type: sh  NVIDIA-Linux-x86-173.14.25.pkg1.run. I'm guessing that is in the terminal. should it work?

[http://www.nvidia.co.uk/object/linux_display_ia32_173.14.25_uk.html](http://www.nvidia.co.uk/object/linux_display_ia32_173.14.25_uk.html) here is the link to look at the install guide.

Yes, you have to out of x for the drivers to install though...if you read the guide I put up in post #2 it tells you how to get them installed, step by step.

---

