---
title: "Screen resolution is wrong"
date: 2009-10-12
forum: General Help
---

### Post by rocklinks on 2009-10-12
Hi Guys,

I'm very new to unbuntu and my first impressions are very high! I was running windows vista but got fed up of it being so restrictive and rubbish! So i thought i would give ubuntu a try. I downloaded the desktop version and installed using the wubi feature. The install went find and im very happy with the end result. The only problem i seem to be having is the screen resolution is 800 x 600 when it used to be around 1024 x 768. I have tried changing in adminstration but 600 x 400 and 800 x 600 are the only 2 options available. Any advice would be great as i really see a good future with me and unbuntu. By the way i have version 9.04!

Thanks

Craig

---

### Post by coldReactive on 2009-10-12
In Ubuntu, go into System > Administration > Hardware Drivers, see if there is a driver available.

---

### Post by rocklinks on 2009-10-12
Hi there,

Thanks for your promot reply!

I have tried that already and it didn't show anything up. Something else i noticed is in the display section is says Unknown monitor dont know if that helps?

---

### Post by wojox on 2009-10-12
Open a terminal and post back this command:

```
lspci | grep VGA
```

---

### Post by coldReactive on 2009-10-12
> **rocklinks said:**
> I have tried that already and it didn't show anything up. Something else i noticed is in the display section is says Unknown monitor dont know if that helps?

Most times, monitors will show as unknown in ubuntu, no matter what.

Do you know what your graphic card is specifically? (hardinfo through terminal might help)

---

### Post by CatKiller on 2009-10-12
Normally, resolution problems are caused by one of the monitor, the graphics card, or the graphics driver not passing the EDID information to X that lets it automatically set the correct refresh rate, and so it defaults to really low values that won't damage any monitors. You can manually set the values for your monitor by putting the VertRefresh and HorizSync ranges in your xorg.conf. You should be able to get these numbers from the manual or specifications for your monitor. These values go in the "Monitor" Section of xorg.conf.

You can edit xorg.conf with ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksudo gedit /etc/X11/xorg.conf
``````
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       aa-bb
        VertRefresh     cc-dd
EndSection

```You'll need to replace aa-dd with the values for **your** monitor.

---

### Post by rocklinks on 2009-10-12
Thanks guys,

I will do the terminal commands one at a time. Here is the results.

00:12.0 VGA compatible controller: nVidia Corporation GeForce 7150M (rev a2)

I am running unbuntu on a laptop so not sure how to find out monitor info?

---

### Post by rocklinks on 2009-10-12
Have looked through manual and cannot find any display settings. I have had trouble in the past with NVIDIA driver. How do i know the driver is installed properly?

---

### Post by CatKiller on 2009-10-12
> **rocklinks said:**
>  I am running unbuntu on a laptop so not sure how to find out monitor info?

Telling us the model number might help us to help you find it...

---

### Post by rocklinks on 2009-10-12
Thanks so much for your help.

Here is a page with my laptop specs 

[http://h10010.www1.hp.com/wwpc/ca/en/ho/WF06a/12139188-78299199-78308301-78308301-78308301-78867421.html](http://h10010.www1.hp.com/wwpc/ca/en/ho/WF06a/12139188-78299199-78308301-78308301-78308301-78867421.html)

Compaq Presario V6000

---

### Post by CatKiller on 2009-10-12
You're right, their listed specifications are somewhat lacking.

```

        HorizSync       30-52
        VertRefresh     50-62

```Might get you the right resolution available (I'm assuming 1280×800), though. The numbers aren't concrete, they're an educated guess, so you might need to adjust them up or down slightly.

---

### Post by rocklinks on 2009-10-12
Mate you are an absolute genious! Worked a treat! Thank you so much for your help!

---

### Post by CatKiller on 2009-10-12
Well, maybe :)

In this case, though, I'm just experienced at solving this particular problem.

Welcome to the community.

---

