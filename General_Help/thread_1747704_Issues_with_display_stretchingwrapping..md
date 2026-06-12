---
title: "Issues with display stretching/wrapping."
date: 2011-05-02
forum: General Help
---

### Post by picard137 on 2011-05-02
The image below shows how the top of my screen is "stretched" and the left side is wrapped to the right side. Also, the pointer position does not seem to know about the stretching (in the picture the pointer is on the calculator, but the tooltip shows the computer things the pointer is on character map).

The problem is fixed when I change the resolution with the ubuntu gui monitor tool. Anytime the screensaver goes on or restart the problem is back and I have to do the resolution change "fix".

Also, using the default driver (nv18?) for my integrated nvidia geforce mx only give me up to 1024x768. Following the instructions on [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution), I added the following to /etc/gdm/Init/Default:
"
xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
xrandr --addmode VGA-1 "1280x1024_60.00"
xrandr --output VGA-1 --mode 1280x1024_60.00
"
This fixed the resolution problem but the "stretch" still has to be fixed every time I turn on the computer. The "additional drivers" tool doesn't offer me the proprietary driver (i think it should be the legacy driver) for some reason.

Im using ubuntu 11.04 with the no effects gnome option. If it helps, lspci gives me:
...
VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX - nForce GPU] (rev a3)
...
Any help would be appreciated. Thanks.

[http://postimage.org/image/4mf38lac]("http://postimage.org/image/4mf38lac")
[IMG]http://postimage.org/image/4mf38lac[/IMG]

---

### Post by lnebrown on 2011-05-17
I'm not really an serious expert here, but I had what sounds like the same stretch problem before.  I have the nvidia geforce mx as well and i believe i read that it does not work with the nv18? driver you quote.  If you search for other nvidia drivers you will see a 96 version, if i remember correctly.  Wish i could tell you for sure, but my upgrade to 11.04 just hosed my computer so i can't exactly look it up right now :)

But once i installed that 96 version driver, it was available in that "additional drivers" tool.

Good luck!

---

