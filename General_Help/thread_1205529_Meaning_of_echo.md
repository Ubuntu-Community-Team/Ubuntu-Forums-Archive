---
title: "Meaning of echo"
date: 2009-07-06
forum: General Help
---

### Post by tsdaniel on 2009-07-06
I already know that echo can be used to make text appear, but I recently stumbled upon a command of somewhat to turn on the thinklight on my IBM. 
The text is "echo 255 > /sys/class/leds/tpacpi\:\:thinklight/brightness". I don't understand how echo is used in this case. Could someone please explain.

---

### Post by lisati on 2009-07-06
> **tsdaniel said:**
> I already know that echo can be used to make text appear, but I recently stumbled upon a command of somewhat to turn on the thinklight on my IBM. 
The text is "echo 255 > /sys/class/leds/tpacpi\:\:thinklight/brightness". I don't understand how echo is used in this case. Could someone please explain.

"echo 255" on its own means "put 255 on the screen". The ">" means "instead of putting the information on the screen, put it in a file or send it to a device". What follows is a file name or a device name.

---

