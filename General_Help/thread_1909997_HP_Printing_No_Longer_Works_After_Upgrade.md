---
title: "HP Printing No Longer Works After Upgrade"
date: 2012-01-16
forum: General Help
---

### Post by neu5eeCh on 2012-01-16
Here's my problem in a nutshell:

My wife had Ubuntu 9.04 (Gnome 2.x) on her netbook. We upgraded to Xubuntu 11.10 so that she could take advantage of some hardware improvements. The problem is that she can no longer print to her HP printer at work. She gets an incessant print error. I'm not at her office, will be later today, so that if specific info is needed I can get that; but I have a hunch the problem is more general than that.

Is there a way to revert to older print drivers? - ones that previously worked?

---

### Post by neu5eeCh on 2012-01-22
Problem solved. 

Printer: **M1217-NFW**

I installed the automatic HP Printer Installer from the HP website:


[http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

Then:

sudo apt-get install hplip-gui

Then:

sudo hp-setup

Follow the instructions.

This correctly installed the printer. HP's software automatically installed the missing dependencies - on my friend's system. On my own system, not knowing HP would automatically install the dependencies, I did it myself. _Worth noting however:_ I tested this software on my friend's venerable HP Laserjet 1000 (an old printer), and it didn't work.  Answers can be found [here]("http://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&ved=0CB4QFjAA&url=http%3A%2F%2Fubuntuforums.org%2Farchive%2Findex.php%2Ft-112556.html&ei=BEAcT4a_L-nY0QHy9czBCw&usg=AFQjCNGEHmiwjMRWPLUxXa8T4T-JmUK0eg"). There seems to be firmware issues with the HP 1000 - so HP's HIPLIP isn't the answer to everything. In truth, anyone using an HP 1000 should get a new printer. A new printer costs slightly more than the ink cartridge (if one buys refurbished printers from STAPLES as I do).

---

