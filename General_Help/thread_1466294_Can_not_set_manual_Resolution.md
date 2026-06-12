---
title: "Can not set manual Resolution"
date: 2010-04-30
forum: General Help
---

### Post by nexoncore on 2010-04-30
My Monitor is a Acer X223HQ which has a native max resolution of 1920 x 1080. I can easily achieve this is windows vista, but on ubuntu I am limited to 1360 x 768.

I have tried manually adding the resolutions to xorg.conf which puts the Xserver in low graphics mode upon restart. Can someone help me with this as I dont want resolution to ruin my experience.

Running Ubuntu 10.04 LTS, graphics GPU is an intel G41 chipset.

---

### Post by Grenage on 2010-04-30
Have a read [here]("http://www.grenage.com/xorg.html").  Fair warning, I wrote it.

---

### Post by nexoncore on 2010-04-30
Did not work, upon logout to restart X server it came up saying the config was errored and I had to either use low graphcis mode or use default.

---

### Post by Grenage on 2010-04-30
Which part, what did you do?  Post your xorg.conf.

---

### Post by nexoncore on 2010-04-30
```
Section "Monitor"
    Identifier "Monitor0"
    VendorName "DCLLCD"
    ModelName "DCL20AT"
    HorizSync 67.16
    VertRefresh 59.96
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -HSync +Vsync
EndSection

Section "Device"
    Identifier "Device0"
    Driver "intel"
    VendorName "Intel 945GM"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device "Device0"
    Monitor "Monitor0"
    DefaultDepth 16
    SubSection "Display"
        Depth 24
        Modes "1920x1080"
    EndSubSection
EndSection

```I couldnt find the acrual vendor name though, the graphics card is built into this motherboard [http://www.gigabyte.com.tw/Products/Motherboard/Products_OverView.aspx?ProductID=3024](http://www.gigabyte.com.tw/Products/Motherboard/Products_OverView.aspx?ProductID=3024)

---

### Post by nexoncore on 2010-04-30
When I came back to my computer I had the desired resolution but a large issue, no windows have borders anymore, and cannot be resized, moved or even minimised.

This is how it looks
[http://i44.tinypic.com/ngwuva.png](http://i44.tinypic.com/ngwuva.png)

---

### Post by nexoncore on 2010-05-01
Managed to get it to work by dropping down to no effects and using ubuntu tweek to add some needed effects. Thanks

---

### Post by Grenage on 2010-05-03
Hi there,

This command 'should' reinstate borders and buttons:

```
metacity --replace
```

---

