---
title: "Reduce Ubuntu's power consumption on laptop"
date: 2010-08-11
forum: General Help
---

### Post by BurningSludge on 2010-08-11
[FONT=Comic Sans MS][SIZE=3]I have Ubuntu 10.04 on a Toshiba Satellite L455D and I can't get anymore than about 2 hours of power. Power save mode doesn't make my battery last much longer. Is there any way to increase the battery life without a huge risk of damaging the hardware. If possible I would like to have my battery last between 3 to 4 hours.[/SIZE][/FONT]

---

### Post by switch10 on 2010-08-11
Dimming the screen, and turning off WiFi will help a bit.  Watching videos, playing games, listening to music, etc. are all going to drain your battery faster.

---

### Post by hayden92 on 2010-08-11
I've always used "powertop" to help save battery life. 
It's pretty easy to use, and doesn't do anything dangerous.

To install it, type:
```
sudo apt-get install powertop
```

---

### Post by hedgeborn on 2010-08-11
Quickest and easiest way would be to lower your screen's brightness and throttle the clock speed.

I did this when I was running 8.10 on my netbook, though since I upgraded to 10.04 I switched to Netbook remix which unfortunately doesn't seem to have the ability to adjust clock speed on the fly or the LM sensors temperature display. :(

Not sure about the full version of 10.04 though. I'm assuming you can still adjust clock speed.

Some of the more technically inclined members could probably tell you how to turn off some processes or make other adjustments through the terminal that may help. For sure dimming the screen and lowering clock speed WILL make a measurable improvement in battery life. Hope that is somewhat helpful.

---

### Post by shrinux on 2010-09-14
You may follow these steps to enhance the battery live:

Install "powertop".
dim the screen brightness.
minimize the usage of multimedia such as video, sound, gaming, etc.
disable visual effects.
use dark background screen (solid black is recommended).
turn off the WiFi whenever possible.
turn off any application that are not in use.

You may create an account and name it "Power Saving" that considers all these simple tweaks if you like.

---

### Post by maestrobwh1 on 2010-09-14
[http://sourceforge.net/projects/jupiter/files/](http://sourceforge.net/projects/jupiter/files/)

Download and install the latest *.deb file. Launch it from the menu.  It will create an applet in your tray, when you right click it, you will see what it does for you:-)

I do have an asus laptop with the superhybrid engine so it even takes advantage of that.

On battery, it does a really nice job, even on my non-asus computer (Old intel IBM thinkpad).

---

