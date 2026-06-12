---
title: "Lucid Lynx Extremely slow"
date: 2010-07-21
forum: General Help
---

### Post by akber on 2010-07-21
I just upgraded from Karmic a few days ago, and one of the first things i noticed upon boot up (which was as promised, much faster) was that everything seemed choppy. 

I use compiz and all the effects and just the general UI of the desktop seems to be as if it is being viewed through a choppy video. Generally the small things are fine like moving the mouse around etc. but should i want to drag a window around the animation is laggy and blurred. 

Is this a known bug so far? Its not the hardware on the laptop because this was not happening before i upgraded. 

Help appreciated, thank you.

---

### Post by bigfatgooglefat on 2010-07-22
Sounds like your graphics card doesn't have the correct driver working. Download the newest driver from your card's vendor if you know who it is, or check for a  version through Ubuntu by going to System --> Preferences --> Hardware Drivers. Worst case-scenario, if your /home drive is on a separate partition, you can just reinstall without reformatting it.

---

### Post by akber on 2010-07-24
I checked that out, but still no luck, it says that i have all my drivers updated to the most recent release. Any other ideas?

---

### Post by hawthornso23 on 2010-07-24
What do you see in hardware drivers. Does it say the proprietary driver is activated and currently in use? It really does sound like a graphics driver issue to me.

Unlike Jaunty or Karmic, Lucid does a very good job of installing the proprietary driver all by itself via hardware drivers. You shouldn't have to go to the ATI site any more. Indeed the last time I tried to install from the ATI site it totally borked my system.

---

