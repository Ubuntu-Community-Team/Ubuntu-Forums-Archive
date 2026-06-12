---
title: "Set Windows as default in dual-load?"
date: 2010-10-18
forum: General Help
---

### Post by supmah5 on 2010-10-18
I would like to set Windows to be selected by default when i start my system (which has both Ubuntu 10.10 and Windows 7 installed). 

Tried some guides online but they suggested for me to change a file in /boot/grub/ named  menu.lst but there is no such file on my system...

---

### Post by JackNocturne on 2010-10-18
Install a package called "Start up manager" in ubuntu **software-center**. From there its easy to configure those options.

---

### Post by Quackers on 2010-10-18
If you install Startup Manager you can set the default boot options in a GUI.
System > Admin > Synaptic Package Manager
and search for Startup manager

---

### Post by supmah5 on 2010-10-18
Lovely! Now it works just like I wanted it. Had some problems finding the program after I installed it, but it was under System > Administration. Thank you guys.

---

### Post by Cavsfan on 2010-10-18
Also check the tutorial in my signature. It appears difficult at first, but if you just follow the directions, you can have a nice background and 
a maintenance free boot up (Grub) screen). I wanted Windows as my default and got tired of changing the default line every time a new 
kernel was installed. This makes it so you never have to touch it. 
Just another idea. :)

---

