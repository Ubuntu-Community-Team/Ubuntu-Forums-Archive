---
title: "problems booting up"
date: 2009-08-17
forum: General Help
---

### Post by aardvarkgenocide on 2009-08-17
i was attempting to run dual monitors with my laptop, for some reason it did not work, and i ended up with bands of color all up and down both of the screens, i shut it off, disconnected the monitor and powered it on, it goes through its normal routine with the ubuntu symbol, with the loading bar under it. when the bar has loaded it goes to a black screen with just a few stripes of color at the top. i handed it over to my brother, and he tried going into recovery mode, and tried xfix, and "dpkg-reconfigure xserver-xorg" on the command line. what else should we try?

graphics card 
ATI Radion X1200 series

i am pretty sure that i am running ubuntu 9.04


none of this will matter, but other basic specs
my processor is an amd turion 64 X2 Mobile (clocked at 2.2ghz)
3gb ddr2
(that is all that i think could possibly be involved, but if you want to know more about the hardware, just say so...)

i am not sure if this already posted... i already created a thread like this but when i refreshed the page, it said that it did not exist, and brought me back to this, with all of my text entered...

---

### Post by wojox on 2009-08-17
Try:
```
sudo dpkg-reconfigure xserver-xorg -phigh
```

Then:
```
sudo reboot
```

---

### Post by BinaryFeast on 2009-08-17
What modifications did you do to begin with?

You don't happen to have a backup of the etc/X11/xorg.conf file from when it worked, do you? If so, then just delete the broken one and rename the backup file (xorg.conf.whatever) to xorg.conf.

---

### Post by aardvarkgenocide on 2009-08-17
my brother said he tried the first reccomendation, but i tried it again, and it still did not work

all i did was i tried to arange vertical dual monitors, and upon logging out, this occoured

oh, and no i had not gotten around to making a backup yet (i have only been using ubuntu for about 2 weeks, so i am still learning everything, and setting stuff up on my laptop...)

edit: (brother) There were two backups that should have worked (one made by the dual monitor setup). Neither fixed the problem.

---

### Post by aardvarkgenocide on 2009-08-17
I fixed it by reinstalling the xserver-xorg package (and all dependents).

---

### Post by wojox on 2009-08-17
Cool man

---

