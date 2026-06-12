---
title: "help webcam installation"
date: 2009-12-29
forum: General Help
---

### Post by remvs on 2009-12-29
I cannot install my webcam for linux. Need help for drivers

Thank You,

remvs

---

### Post by lrcaballero on 2009-12-29
try the following:

Applications/Accessories/Terminal

In the terminal do the following:

CODE:
sudo modprobe uvcvideo

sudo apt-get install cheese

cheese

If it doesn't open go to Applications/Sound & Video/Cheese

Luis.....

---

### Post by arvevans on 2009-12-29
First you have to help us help you:
[LIST=1]
[*]What type of webcam is it?
[*]Where have you looked for drivers?
[*]Have you performed a search for your particular webcam on this forum/group?
[*]Is it a USB webcam, or an older serial-port one?
[*]If it is a USB connected webcam, have you already performed "lsusb" from a terminal prompt to see if your webcam hardware is being recognized?  If yes, please show the results of "lsusb" so we know how to help you further.
[*]Have you researched for Linux Compatibility of your particular webcam?  Was it on the list?
[/LIST]
_._

---

