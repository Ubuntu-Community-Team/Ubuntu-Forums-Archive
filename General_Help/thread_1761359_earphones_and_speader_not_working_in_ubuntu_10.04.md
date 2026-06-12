---
title: "earphones and speader not working in ubuntu 10.04"
date: 2011-05-18
forum: General Help
---

### Post by roronoazoro89 on 2011-05-18
Hi, well i have a problem with my SONY VAIO laptop, the model is VPCEB1EL. When i use windows, earphones and speakers works perfectly, but when i change to LINUX UBUNTU 10.04 sound don't work, i have other headphones that i connect through a USB PORT, and it works perfect, but i really want to fix my normal earphone port, because i need it in order to connect audio to my new 50 inches plasma LG. 
I can clearly see my laptop screen in the TV screen,  but i need audio to hear videos. 
please someone help me. i will appreciate it

---

### Post by SynonM on 2011-05-18
Hi,

open "terminal"
type "alsamixer" 

use your arrow keys find the devices that show "mm" 
highlight one at a time and hit the  "m" to unmute --> "00"
until your headphones work.
*** CAREFUL You might have to hit "m" again quickly to mute --> "mm"
because sometimes you'll get a high-pitched loop. (be ready)

or

right click the sound/audio icon (usu. top right)
select "sound preferences" 
see if your hardware is recognised... if so 
enable the proper input/output devices

and done

:popcorn:
if this worked don't forget to put as [solved]

---

### Post by SynonM on 2011-05-18
bump.... fixed?

:popcorn:

---

