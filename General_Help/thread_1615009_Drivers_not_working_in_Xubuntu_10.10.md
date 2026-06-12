---
title: "Drivers not working in Xubuntu 10.10"
date: 2010-11-06
forum: General Help
---

### Post by ChaosChris2009 on 2010-11-06
Hello, the drivers aren't working in Xubuntu 10.10 on my Compaq Presario CQ-60 Notebook Laptop

I installed Xubuntu this morning without an internet connection, all I can pretty much do is boot into the OS, I have no sound, no wireless, no drivers are working at all in Xubuntu 10.10

Help

---

### Post by dino99 on 2010-11-06
into a terminal:

sudo apt-get install -f
sudo dpkg --configure -a

if you can update using the main server its better

about sound, check card/chipset detection, then settings in the properties

---

### Post by alzaf on 2010-12-06
Concerning sound not working, you may want to try this:

   1. Add the Mixer (volume control) to your menu panel (if you haven't got it on already)
   2. Click on Mixer
   3. In Sound card drop down menu select: Playback: Internal Audio Analog Stereo (PulseAudio Mixer)
   4. Click on Select Controls (The Select control dialog appears.)
   5. Click on Master. This will be now be ticked.
   6. Press Close button
   7. Unmute the Master Control

---

