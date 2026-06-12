---
title: "Make xrandr settings permanent"
date: 2012-08-15
forum: General Help
---

### Post by euphoric_anomaly on 2012-08-15
After many frustrating attemps to configure xorg.conf via text  editor (and always getting a blank page), I decided to give xrandr a whirl.

12.04 does not detect my monitor (Dell 1708FP), and I have dreaded Intel 945g chipset onboard graphics. Ubuntu was giving me 1024x768 and that was it.

I was able to use 1280x1024 by using the following commands with xrandr:

xrandr --newmode  "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
xrandr --addmode VGA1 1280x1024_60.00
xrandr --output VGA1 --mode 1280x1024_60.00

I have to run this in terminal everytime i log in, otherwise it reverts back to 1024x768 and gives me an error message about how it can't "find" or "use" the 1280x1024 setting.

Is there anyway to make a script that will run when I log-in or is there a way to make these setting permanent?

Thanks in advance

---

