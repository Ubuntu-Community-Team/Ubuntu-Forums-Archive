---
title: "HDMI No sound"
date: 2011-12-10
forum: General Help
---

### Post by jmacx81 on 2011-12-10
When I plug an HDMI cable into my computer, I get no sound and the video speed plays at like double or triple speed. Also when I plug headphones in during non HDMI setup I get sound in the headphones and PC speakers.. How can I turn off the PC speakers?

---

### Post by pqwoerituytrueiwoq on 2011-12-10
go into sound preferences and look in your output tab

---

### Post by linuxman94 on 2011-12-10
Yeah, have a look at the sound options output tab.  It should have an option for HDMI output, make sure that is selected and try it again.  If that doesn't work, tell us what graphics card you have.

---

### Post by jmacx81 on 2011-12-10
Sorry, I should have stated that everything was looking normal in the sound settings, the only issue with that it is a real pain to get the sound working again and the video speed back to normal after you try switching away from HDMI

This is what I get for my graphics card "Gallium 0.4 on AMD RV710"

---

### Post by linuxman94 on 2011-12-11
Looks like your using the open source Gallium drivers.  Installing the fglrx driver should solve your problems.  Just open up *Additional Drivers* and activate the AMD Proprietary Driver.  Reboot and see if that solved the problems.

---

