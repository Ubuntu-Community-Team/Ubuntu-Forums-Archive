---
title: "Sudden onset of Blurriness"
date: 2011-05-27
forum: General Help
---

### Post by Mr Fredrick on 2011-05-27
Hi All,

I am running Natty on my laptop when suddenly everything on the screen has gone blurry.

How can I determine if this is an Ubuntu or a hardware problem?

Thanks in advance,

MrFred.

---

### Post by linuxinstalledfromhdd on 2011-05-27
Try going to "Monitors" and adjusting the screen resolution.

---

### Post by Mr Fredrick on 2011-05-27
I reset the resolution but its had no effect

---

### Post by linuxinstalledfromhdd on 2011-05-27
I've had the blurry problem before, and I tried all of the different resolutions until the blurriness stopped. Did you try that?

---

### Post by Mr Fredrick on 2011-05-27
Yes, I have tried different resolutions but even they are blurry. It seems to be a particular form of blurriness, Check the image I posted.

---

### Post by linuxinstalledfromhdd on 2011-05-27
Can you give a basic run down of the type of hardware and specs you have running?  What kind of computer is this? How is old is it?

---

### Post by Mr Fredrick on 2011-05-27
My system specs are part of my signature and therefore included in all my posts.

Attached in another screen-shot, note the *type* of blurriness.

---

### Post by linuxinstalledfromhdd on 2011-05-27
Did this issue exist in Maverick 10.10 with the graphic drivers installed?

---

### Post by Mr Fredrick on 2011-05-27
NO, this issue developed suddenly a few hours ago whilst using Natty.

---

### Post by LowSky on 2011-05-27
If you look around the room is anything else blurry? Sorry I just had to.
The screen shot doesn't seem blurry to me in the pictures. The quality seems low, but you saved it as a jpg so that could be just how it was saved.

Go to nvidia settings and make sure the refresh rate is correct. form terminal open with sudo so you can save the settings to xorg.


If the screen goes blurry it could be a sign of the monitor is failing. It is a laptop check the ribbon cable for cracks.

---

### Post by Mr Fredrick on 2011-05-27
The blurriness seems to be caused by every fourth or fifth vertical line being redrawn one or two lines too early. 

Can anybody help me diagnose this problem? How can I tell if I have suddenly developed a hardware problem?

---

### Post by Mr Fredrick on 2011-05-27
In an attempt to diagnose this problem I ran memtest86+ from the GRUB menu. Suddenly during the test the blurriness disappeared and I can now read the screen again!

Also checking back on the screen-shots that I attached to my previous posts, they seem OK also, so maybe its not the memory but the monitor itself.

---

