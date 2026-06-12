---
title: "new laptop, Hp pavillion dv6t quad, headphones not working right"
date: 2011-06-18
forum: General Help
---

### Post by Mr Nemo on 2011-06-18
So i just bought a new HP pavillion dv6t quad core laptop. After installing ubuntu everything seemed to work right out of the box, except for the headphones. The laptop comes with two jacks to plug headphones into and the laptop speakers will not turn off fully when only one jack is occupied. I've been looking for a workaround, but I haven't had any luck finding anything. Any help would be appreciated.

---

### Post by Mr Nemo on 2011-06-18
Found the solution. 

open up /etc/modprobe.d/alsa-base.conf  with gedit

add line "options snd-hda-intel model=yourcomputermodelhere" (in my case it was hp-dv6t) to the end of the file

restart

worked perfectly for me

[http://ubuntuforums.org/showthread.php?t=1256903](http://ubuntuforums.org/showthread.php?t=1256903) - some more info

---

