---
title: "Setting resolution"
date: 2011-11-29
forum: General Help
---

### Post by ninety niner on 2011-11-29
I AM AN ABSOLUTE BEGINNER.  I HAVE INSTALLED 11.10 ON AN EI SYSTEM LAPTOP.
THE DISPLAY COVERS ABOUT A THIRD OF THE SCREEN. i HAVE GONE TO SETTINGS --DISPLAY BUT IT IS NOT POSSIBLE TO CHANGE THE RESOLUTION OF 640*480. PLEASE HELP

---

### Post by jerrrys on 2011-12-01
There are several threads on this

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=screen+resolution+oneiric+11.10&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=screen+resolution+oneiric+11.10&sa=Search&cof=FORID:9)

But the simplest of fixes works for me.  I just add the extra resolution package.

Open a terminal and enter:
sudo apt-get install screen-resolution-extra

---

### Post by raja.genupula on 2011-12-01
+1 
Here a tutorial for you

[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

### Post by jerrrys on 2011-12-01
Hi raja:

that link is dated and will not work.  GDM has been replaced with lightdm.

---

### Post by grahammechanical on 2011-12-01
Did you activate a proprietary driver using the Additional Drivers Utility? If so, then a configuration utility for that driver would also have been installed and the Displays utility in System Settings disabled.

If this has happened in your case then you can find the configuration utility by opening the dash and searching the installed applications.

Regards.

---

