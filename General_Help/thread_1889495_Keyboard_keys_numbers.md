---
title: "Keyboard keys numbers"
date: 2011-12-01
forum: General Help
---

### Post by JazzPotato on 2011-12-01
I'm currently trying to fix a brightness key control problem. I am wondering if the brightness keys are being recognized. I want to add the brightness keys to /etc/rc.local so i need to know how the keys are numbered. Its a standard British keyboard on a 15" laptop, without the group of 6 keys with "ins" and "home" on it and with numeric keypad. 
 Are the keys numbered from top-right or what?
Thanks for the support

---

### Post by mcduck on 2011-12-01
There's no standard to the key number order (like "left to right" or anything like that), at least as far as I know.

However you can open a terminal and run "*xev*" and then press the keys, and as long as the keys are detected in any way it should print you the key codes.

(just try not to move the mouse when doing this, as xev will also report mouse movements and any other input)

IF you need to press some function switch key to acces the brightness keys, this migth not work depending on how the keys are implemented on your system. But it's worth a try anyway...

---

