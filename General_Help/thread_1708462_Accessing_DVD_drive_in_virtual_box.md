---
title: "Accessing DVD drive in virtual box"
date: 2011-03-16
forum: General Help
---

### Post by HorseBox on 2011-03-16
Its been a long time since I've loaded my Windows partition cuz I've been able to run any windows programs on a guest with virtual box but I can't figure out how to access the DVD drive with the windows host. I can get it to detect any hardware thats connected by USB by going into settings and selecting the USB tab then adding filters but the DVD drive isn't connected by a USB cable so this doesn't work for it. I searched and found a few threads but the people replying just recommended that the OP dual boot and load the CD with his windows partition. Thats a pain in the *** and I can probably find some roundabout way to run the program with WINE or by dragging the contents of the CD into the Windows hosts hard drive then figuring out how to bypass the fact it wont run unless it detects the CD in the drive but surely you can get Windows guests to just read the CD drive.

EDIT: Its pretty ridiculous that I figured out the problem 10 seconds after making this thread but I did so heres how I did it: Went into Settings > Storage then there was a field labelled IDE controller or something and beside it was a dropdown menu that had a .ISO selected. The other option in the dropdown menu was my DVD drive so I selected it, ran the host and now it detects the DVD drive :D

---

