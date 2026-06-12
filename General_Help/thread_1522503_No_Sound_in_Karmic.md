---
title: "No Sound in Karmic"
date: 2010-07-02
forum: General Help
---

### Post by The_Pheonix_Project on 2010-07-02
I just upgraded from Intrepid to Jaunty and then from jaunty to Karmic via update manager -d, now I cannot get my sound to work-I am running a gigabyte GA-X48T-DQ6 motherboard with I believe a 7.1 channel REALTEK chipset...can anyone tell me how to get my sound working again?  Also I posted under Installations and Upgrades regarding the fact that this upgrade left my kernel unconfigured...ANY HELP WILL BE GREATLY APPRECIATED!

---

### Post by Oolongtea on 2010-07-02
Create a launcher on your desktop by left clicking and enter this code in the command slot. There will be a volume control in the top right corner of your screen. Feel free to delete the launcher after you see the volume control.
```
gnome-volume-control-applet
```

---

### Post by The_Pheonix_Project on 2010-07-02
I did this but nothing appeared, tbe I tried just running the command in terminal and it said gnome-volume-control-applet already running...???

---

### Post by Oolongtea on 2010-07-02
do not do terminal. Create a launcher (desktop icon) and put the code in as the command. click it and the applet should appear.

---

### Post by haywirepc on 2010-07-02
I kind of hate to say this because its certainly not the right way to do things but...

I always keep a couple of soundblaster live pci cards around. Its such a common card that almost every os and linux distro supports it. So any problems with onboard audio, slap in the sblive and no more hair pulling.

if all else fails, try that and just remember to disable onboard sound in your bios.

Steven

---

