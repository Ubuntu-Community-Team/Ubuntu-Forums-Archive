---
title: "Ubuntu pSX issues Help Please."
date: 2011-08-28
forum: General Help
---

### Post by CalvinCarpenter on 2011-08-28
I am downloading and trying to use pSX emulator I am useing this guide. 

[http://maketecheasier.com/guide-to-playstation-emulator-on-ubuntu/2008/03/19](http://maketecheasier.com/guide-to-playstation-emulator-on-ubuntu/2008/03/19)

I get to this step "Another window will appear to allow you to select the bios, click on the ‘scph1001.bin’ and click OK." 

and I select the Scph1001 File and click ok  and then aparently the Default playstation screen should appear then I Click File Load Rom, HOwever this default screen never appears, I have got every step fine right up untill this screen should appear but dosnt all prior screens work fine like the Selection of language and  bios not being found and then selecting it.

any help I could get to making this work would be greatly appreciated.

---

### Post by jerrrys on 2011-08-28
open a terminal and enter:

scph1001

what happens?

---

### Post by CalvinCarpenter on 2011-08-28
cali@HomeLaptop:~$ scph1001
scph1001: command not found
cali@HomeLaptop:~$

---

### Post by jerrrys on 2011-08-28
what about

pSX

---

### Post by CalvinCarpenter on 2011-08-28
cali@HomeLaptop:~$ scph1001
scph1001: command not found
cali@HomeLaptop:~$ pSX
pSX: command not found
cali@HomeLaptop:~$

---

### Post by jerrrys on 2011-08-28
reboot?

---

### Post by CalvinCarpenter on 2011-08-28
still nothing. everything seems to be installed correctly, I have the schp1001 file in the pSX Bios folder not sure why it dosnt actully load the final step.

its located in my home folder, not sure if that matters  

home/cali/pSX/bios

---

### Post by jerrrys on 2011-08-28
we have tried the simple things.  now i think your going to have to go here for further help.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=pSX+emulator&sa=Search&cof=FORID:9#821](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=pSX+emulator&sa=Search&cof=FORID:9#821)

good luck

---

### Post by CalvinCarpenter on 2011-08-28
..... which one of these results do i go to?

---

### Post by CalvinCarpenter on 2011-08-28
After Much trouble Shooting I got the Play station screen to come up I did this buy downloading all of these programs.

	OpenGL   (GL TUTORIAL)  [http://ubuntuforums.org/showthread.php?t=345177](http://ubuntuforums.org/showthread.php?t=345177) 	ALSA  (ASLA tutorial)  [http://www.stchman.com/alsa_update.html](http://www.stchman.com/alsa_update.html)
 GTK  git clone git://git.gnome.org/gtk+     AND   git clone git://git.gnome.org/glib 	GTKGLEXT  git clone git://git.gnome.org/gtkglext 	libxml2   git clone git://git.gnome.org/libxml2


I found them by googlin each program and then finding the terminal code for each

---

### Post by His Royal Freshness on 2011-09-06
> **CalvinCarpenter said:**
>  (ASLA tutorial)  [http://www.stchman.com/alsa_update.html](http://www.stchman.com/alsa_update.html)I'm also having issues with pSX, so I did everything in the above post, including what I quoted.  ~now I have no sound~

Can I reverse this or what do I have to do to hear my computer again.

---

### Post by His Royal Freshness on 2011-09-06
derp

---

