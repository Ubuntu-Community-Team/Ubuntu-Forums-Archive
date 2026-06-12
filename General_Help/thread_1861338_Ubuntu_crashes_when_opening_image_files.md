---
title: "Ubuntu crashes when opening image files"
date: 2011-10-15
forum: General Help
---

### Post by mprabuw on 2011-10-15
I have a problem opening image files on Ubuntu 11.10 that made the Ubuntu itself crashes and made me to do a hard reset to the computer. (press the power button 5 seconds to turn off). 

I have some images of *.png files of webpage saved from screen grab. Most of them have very long height size. (usually 1000x20000 pixels, depends on the contents of the web itself).

I don't think they're all big files since it's only 6 MB. However it's very wide image file.

So the problem happens when I trying to open those files in image viewer program which comes with standard package of Ubuntu installer. the image loading in the bottom right is finished. But, after that, the mouse is starting to move slowly and not responding at all. It's not responding to any shortcut in the keyboard. The mouse also can't move. The Ubuntu's crashed!! I have to do a hard reset then..

When I trying to open it in Windows, it's normal. There's nothing wrong with the files. Here are some properties of the files: (1007 x 29110 pixels, PNG, 5,99 MB), (1007 x 17942 pixels, PNG, 6,14 MB). 

Could someone help me?

My hardware specification:
Netbook, Atom N550 1.5 GHz 1mb L2 cache, Memory 2GB.

---

### Post by Safarir on 2011-10-16
I have the same problem with my DellV13

I am using Gnome-Shell

---

### Post by Gordon D on 2011-10-18
Same problem. Using Gnome, but also fails when using UBUNTU. Upgraded from 11.04 to 11.10. Is there a bug raised for this yet?

---

### Post by crazy bird on 2011-10-18
To all:
Open a terminal and in that terminal open your imageviewer, i.e.: if you're using Gimp, just type gimp in the terminal. When the program is running, open an image. If the program crashes, there should be some output visible in the terminal. Select that output (Shift+Ctrl+C) and paste it here. So we can see what happens when your imgaveviewer crashes.

---

### Post by Gordon D on 2011-10-18
I opened eog via terminal and tried this. The system become completely unresponsive and requires a hard reset (holding power button for 5 seconds). There is no output on the terminal screen.

I have raised a bug for this Bug #877279

---

### Post by crazy bird on 2011-10-19
> **Gordon D said:**
> I opened eog via terminal and tried this. The system become completely unresponsive and requires a hard reset (holding power button for 5 seconds). There is no output on the terminal screen.
 
I have raised a bug for this Bug #877279
 
Looks like there's more going on than Eog. It seems to me that you have a memory problem. Can you run memtest or a similar tool?

---

### Post by tommy13v on 2011-11-23
I am having the exact same issue as you are. I will file a bug report and see what happens.

---

