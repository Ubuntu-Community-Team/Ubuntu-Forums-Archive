---
title: "High CPU usage in 12.04: Xorg"
date: 2012-07-21
forum: General Help
---

### Post by vasa1 on 2012-07-21
[http://ubuntuforums.org/showthread.php?t=2028878](http://ubuntuforums.org/showthread.php?t=2028878) is a thread started by QIII but about QQ.

I notice that I get can CPU usage of > ~12% attributed by top to Xorg by selecting and then copying text in LibreOffice Calc (ver. 3.5.4.2) to get the "marching ants" (marquee). As long as the ants are marching, the CPU usage by Xorg remains high.

I guess it is expected behavior since the screen is being redrawn. But does anyone know if there's some other way to indicate that cells have not only been selected but also copied in LibreOffice?

I think Google Docs handles things a bit more elegantly. Cells that are merely selected have a static blue border but if they're also copied, the border turns orangy.

---

### Post by vasa1 on 2012-07-23
The workaround is to turn off "use anti-aliasing" in Tools, Options, View, **Graphics output**.

I don't know what the downside is.

---

