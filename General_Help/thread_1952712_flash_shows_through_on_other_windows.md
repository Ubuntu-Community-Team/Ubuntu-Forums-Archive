---
title: "flash shows through on other windows"
date: 2012-04-04
forum: General Help
---

### Post by jejones3141 on 2012-04-04
Since this past Sunday, I've noticed something strange: if I have a browser open to a Flash video, the Flash video shows through the strokes of the characters of other windows.

I have Ubuntu 11.10 running on an AMD 64-bit CPU, with an nVidia 560Ti graphics card. I was using 280.13, nvidia-current, but tried 295.20, nvidia-current-updates, to see whether it made a difference. (It didn't.) I have adobe-flashplugin 11.2.202.228-0oneiric1 installed.

To show the problem: fire up your favorite browser, and go to a page that has a flash video embedded. (instapundit.com is a good choice, since it almost always has an embedded flash video). Scroll down to the embedded flash video on the browser. Fire up another window--as long as it has rendered text, it will do, though the best way I've found is to fire up xfce-terminal. It will show the flash video on the background. Move the window around and you'll see the flash showing through. The browser window can be minimized, and the tab with the embedded flash video doesn't have to be the selected one on the browser. The browser window's position doesn't appear to matter. Close the tab with the embedded flash video, and the effect vanishes.

So... the three possible culprits that come to mind are the Flash plugin, the graphics card driver, or the graphics card itself. How should I start to determine the cause?

---

### Post by sdowney717 on 2012-04-04
try turning off hardware acceleration, right click to see that.
The last flash released for Linux is buggy, a nice parting shot by Adobe as Adobe says this is the last one.

I also cant see flash stock charts at yahoo finance
endlessly waits.
[http://finance.yahoo.com/echarts?s=EXC+Interactive#symbol=exc;range=5d;compare=;indicator=volume;charttype=area;crosshair=on;ohlcvalues=0;logscale=off;source=undefined;](http://finance.yahoo.com/echarts?s=EXC+Interactive#symbol=exc;range=5d;compare=;indicator=volume;charttype=area;crosshair=on;ohlcvalues=0;logscale=off;source=undefined;)

---

### Post by jejones3141 on 2012-04-04
> **sdowney717 said:**
> try turning off hardware acceleration, right click to see that.
The last flash released for Linux is buggy, a nice parting shot by Adobe as Adobe says this is the last one.

Aargh. Right clicking indeed brings that up, but clicking to turn off the hardware acceleration appears to have no effect--the checkmark remains checked.

---

### Post by sdowney717 on 2012-04-04
make the video full screen, then click it off.

---

### Post by jejones3141 on 2012-04-05
> **sdowney717 said:**
> make the video full screen, then click it off.

Thanks! That seems to have done the trick.

---

