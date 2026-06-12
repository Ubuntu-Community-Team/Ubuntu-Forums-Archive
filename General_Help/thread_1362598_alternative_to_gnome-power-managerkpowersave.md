---
title: "alternative to gnome-power-manager/kpowersave?"
date: 2009-12-23
forum: General Help
---

### Post by cthulhu_54 on 2009-12-23
I'm looking for an alternative to gnome-power-manager or kpowersave, since I don't want to install a bunch of gnome/kde dependencies. The functions I'm after is the same as are in gnome-power-manager:
-Monitor my battery, alerting me how much time is left
-Control screen brightness
-Control what is to happen when I close the lid of my laptop

Has anyone any ideas or suggestions?

---

### Post by Elfy on 2010-01-20
bump on the move

---

### Post by Simian Man on 2010-01-20
Xfce has a power manager, but I'm not sure how many xfce dependencies it has.

Edit:
Just checked and it depends on the xfce4-panel (for the brightness applet probably), xfconf (for storing your settings) and a few librries.  This is on Fedora 12.

---

### Post by cthulhu_54 on 2010-01-21
What's Xfce's PowerMangager called? (sorry for being lazy)

---

### Post by Matt Brooks on 2010-06-27
i have the almost the same problem. i need an alternative to gnome-power-manager because in my opinion it doesnt provide a good enough power profile manager so that i can set the CPU and hardware usage as well as display brightness so that when i am on AC power my laptop can be running at 100% everything, so to speak, and when on battery, the display is automatically at a lower brightness, the CPU works at say 800 mgz, and i can disable different hardwares (the part about hardwaer is not totally necessary)

just something to broaden the research that might help others not just me.

EDIT: to get the xfce4 power manager run this command:  
                 
sudo apt-get install xfce4-power-manager

---

### Post by cthulhu_54 on 2010-08-04
You might want to take a look at laptop-mode-tool, it's perfect for the things you want (I think).

I have that in combination with cpufrequtils and when I'm on battery I scale down my CPU, computer is still as fast, but battery lasts a lot longer. 

spinning down the hard drive doesn't do much though.

---

