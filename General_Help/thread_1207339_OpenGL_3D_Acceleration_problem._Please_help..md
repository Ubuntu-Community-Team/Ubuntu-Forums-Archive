---
title: "OpenGL 3D Acceleration problem. Please help."
date: 2009-07-08
forum: General Help
---

### Post by rocket16 on 2009-07-08
[SIZE=3][FONT=Comic Sans MS]Hello to all in the forum. I've recently joined, and am a novice in Linux Computing. I have a Compaq Presario 7500 Desktop at my home, with ATI Radeon Xpress 200 Series and Intel Inside Pentium 4. I was earlier using Windows XP and Vista, but I have decided to use Ubuntu as my primary Operating System. All is working nicely in Ubuntu, but only one problem is there, that is my OpenGL Acceleration is not working. By default, all 3D Games are running, but with incredibly low performance. But for example, when I chose to play Ubuntu Chess on 3D, it fails to start. I have been facing this problem for several days. I installed several drivers, such as Xorg, XVesa, and ATI Drivers for linux, but still tthe problem exists. Many a times, Ubuntu got corrupted for installing wrong drivers. I am only a novice in Linux, but I have taken several steps to popularise Linux (esp. Ubuntu and Puppy) in my localities (I am a dwelle of India, in a remote and small town), where most are still sticking to Windows. We have set up Linux Systems in our clubs, and are trying hard to popularise it in India. But strictly speaking, when we install Windows Vista on the same system, the Graphics are fine. So, is there any solution? Thanks to anyone, who'd like to help.[/FONT][/SIZE]

---

### Post by rocket16 on 2009-07-08
[LIST]
[*][SIZE=3]And I forgot to mention, I am only 12, and am primarily interested in Science. So, it will be very kind of you, to suggest a relatively easier process. Thank you again.[/SIZE]
[/LIST]

---

### Post by 3rdalbum on 2009-07-08
The ATI proprietary driver "Catalyst" no longer supports the ATI Radeon Xpress 200. Installing Catalyst on your system will probably stop your graphics from working at all.

The open-source ATI driver, used by default on Ubuntu, is capable of basic 2D operation of your graphics chip, but might not give you 3D acceleration.

If you need 3D acceleration, you have two options:

1. Buy an Nvidia graphics card (your computer probably only has AGP ports for graphics, so you will need an older Nvidia card that uses AGP). This will give you much better 3D performance than you ever got with the Xpress 200

2. Use Ubuntu 8.10, which works with the older version of the ATI Catalyst driver that can support your hardware.

---

### Post by rocket16 on 2009-07-08
Thank you Sir, for your earnest help. I will therefore buy a NVidia Graphic Card. I received great help from your Suggestion.

---

