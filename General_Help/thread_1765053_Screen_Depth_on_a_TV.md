---
title: "Screen Depth on a TV"
date: 2011-05-22
forum: General Help
---

### Post by mackedo on 2011-05-22
Odd question, not even sure I'm wording it correctly.  I'm still rather new to Linux, and have searched a number of sources for this answer in vain.  I'm running a computer on a 1080p television, using HDMI as the connection cable.  On a fresh boot of Ubuntu (and Puppy), the screen fits perfectly, without any black areas or cropping of the edges.  But, without the Nividia driver, it also has no sound, as the sound is routed through the video card via the HDMI.  When I do install the drivers, the screen depth suddenly stops working.  it either has major areas that are black and not used, or the edges are so heavily cropped off that it's close to impossible to use it.  I remember the older Nvidia drivers used to have a function that I could use a GUI to resize the screen manually, but I can't find that feature in the current drivers.  Is there ANYTHING that can be done to fix this?

---

### Post by Hedgehog1 on 2011-05-22
To fix the cropping (Overscan) adjust the overscan compensation:

[IMG]http://imageshack.us/m/18/4561/screenshotnvidiaxserver.png[/IMG]


To get audio over HDMI:  [**_Natty How To: Audio over HDMI for NVidia_**]("http://ubuntuforums.org/showthread.php?t=1741294")

***The Hedge***

:KS

---

### Post by mackedo on 2011-05-22
I'd tinkered with it for 2 hours now, and can't find the overscan compensation in the driver settings, as your screen shot showed.  Does it work in 10.04, or do I need to upgrade to 10.10/11.04?

---

### Post by mackedo on 2011-05-22
Ok, I managed to find the Overscan bar.  it did not show up before, but after hitting "save to Xconfig", I got an error message, and now the bar shows up, and I can adjust it to the perfect size.  The issue I have now is it doesnt KEEP that size when I restart.  It goes back to the default, and I have to go back into the video config to resize it.  is there some way to heep the changes permanent?

---

