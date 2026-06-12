---
title: "Screen Resolution"
date: 2010-12-09
forum: General Help
---

### Post by Mathanv on 2010-12-09
Today for some weird reason, the resolution of my screen on Ubuntu is messed up. Everything is big and not sleek any more like before. I checked the resolution settings and they were all fine and were the same settings as before. Everything was fine before , today it just suddenly changed to this size for some reason. Can anyone help me with this?

[IMG]http://img109.imageshack.us/img109/8393/screenshot4s.png[/IMG]

---

### Post by I'mGeorge on 2010-12-09
have you've tried configuring /etc/X11/xorg.conf . Go to Section "monitor" and check the resolution parameter from "PreferredMode"

---

### Post by coffeecat on 2010-12-09
Your screenshot looks like a normal fairly small screen - perhaps a laptop - so do you mean you have a magnified small screen on a large monitor? What is the size of the monitor, what is its normal pixel resolution and what resolution is showing in System > Preferences > Display?

---

### Post by Mathanv on 2010-12-09
> **I'mGeorge said:**
> have you've tried configuring /etc/X11/xorg.conf . Go to Section "monitor" and check the resolution parameter from "PreferredMode"

**I have very minimal/hardly any experience with Linux, so I don't know how to pull that up ^.**

> Your screenshot looks like a normal fairly small screen - perhaps a  laptop - so do you mean you have a magnified small screen on a large  monitor? What is the size of the monitor, what is its normal pixel  resolution and what resolution is showing in System > Preferences  > Display?     

**I have a 17" Monitor and its a Desktop and yh, I have a smaller screen magnified. It's not smooth and sleek like I had it before. The normal resolution should be 1024 X 768.**

[COLOR=Blue]**This is what I have in the monitor settings: **[/COLOR]

[IMG]http://img23.imageshack.us/img23/3010/screenshotrp.png[/IMG]

---

### Post by coffeecat on 2010-12-09
> **Mathanv said:**
> **I have a 17" Monitor and its a Desktop and yh, I have a smaller screen magnified. It's not smooth and sleek like I had it before. The normal resolution should be 1024 X 768.**

Your screenshot shows exactly what I would expect from a 1024x768 display. However, a 17" monitor would have a resolution of 1280x1024 if a non-widescreen one or something like 1440x900 if widescreen. I suspect your monitor is a 1280x1024 one and the appearance would not be good if the graphics card output is 1024x768. Go back to Monitor Preferences and click on the Resolution drop-down. Can you select 1280x1024?

---

### Post by Mathanv on 2010-12-09
> **coffeecat said:**
> Your screenshot shows exactly what I would expect from a 1024x768 display. However, a 17" monitor would have a resolution of 1280x1024 if a non-widescreen one or something like 1440x900 if widescreen. I suspect your monitor is a 1280x1024 one and the appearance would not be good if the graphics card output is 1024x768. Go back to Monitor Preferences and click on the Resolution drop-down. Can you select 1280x1024?

Ah sorry, I was meant to say 1280x1024. There isn't an option for 1280x1024 on the resolution drop-down.

---

### Post by coffeecat on 2010-12-09
I notice that Monitor Preferences is saying 'unknown' for your monitor, although that is not unusual. Try clicking on the 'Detect monitors' button.

The video driver relies on the EDID information provided by the monitor. Sometimes this is faulty, but it's odd that the resolution was OK and now isn't. Have you, by chance, installed a different video driver? What video card do you have?

---

### Post by advet on 2010-12-09
Had the same problem. Strangly enough it was the cable from graphics to lcd, which was not connected hard enough.

---

### Post by Mathanv on 2010-12-09
> **advet said:**
> Had the same problem. Strangly enough it was the cable from graphics to lcd, which was not connected hard enough.

This was the problem!#-o its fixed now.
Really should have checked the cables before posting here, really sorry.

Thank you Coffeecat for the quick responses aswell as advet with the solution!

---

### Post by coffeecat on 2010-12-09
> **Mathanv said:**
> Really should have checked the cables before posting here

No worries. I'm glad it's solved. In fact, it's useful to know this. Perhaps 1024x768 is a fall-back resolution when the EDID data gets garbled or is non-existent. I shall bear that in mind for my own use. :)

Whatever, I was hunting around and came across this link below which I'm going to add to my bookmarks. It might be useful for future reference when it's not the cable at fault.

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

Good luck!

---

