---
title: "Graphics bug (solve this quick or I'll stop using this system)"
date: 2009-11-14
forum: General Help
---

### Post by mariuszp on 2009-11-14
In Ubuntu 7.10 and 8.10, I've had a bug - when I moved a window, it went black. When I scrolled, then instead of scrolling, text below or above, or really, EVERYTHING above or below went over the stuff I was seeing first, once this bug occured with one program, it started occuring in everything! In Ubuntu 9.04, there was no such bug. When I upgraded to Ubuntu 9.10 - I'VE GOT THIS AGAIN!!! Are you using a different version of GNOME for Ubuntu x.10 than for x.04? Then I'll give you a tip - start using the x.04 one for EVERY UBUNTU THAT COMES OUT. I found a solution for this problem once, but it didn't work - the solution was to change the window manager. Another one was to install the right driver. Still didn't work. I've got NVIDIA graphic card.

P.S. The reason for the driver solution not working is that it said I can't have drivers................................................................

---

### Post by SPr on 2009-11-14
"(solve this quick or I'll stop using this system)" Is that supposed to be some kind of threat? *Shrugs*

Try installing the nVidia drivers again.

---

### Post by jeb800e on 2009-11-14
Try updating your system. That may help.

If that doesn't work, try searching for the proprietary driver for your graphics card again and reinstalling it. 

If that doesn't work, restart your system and boot up into the GRUB screen first (by clicking "Esc" right before your Ubuntu starts to graphically load) and choose an older kernel.

If that doesn't work, boot back into normal mode and right-click on your desktop, click "Change Desktop Background",  and click on "Visual Effects". Now, click on the "None" selection, if not already chosen. Click "Close"

If none of these work, try doing a fresh install of Ubuntu 8.04 LTS Hardy Heron. This is the version least likely to have complications.

---

### Post by ikacer on 2009-11-14
> **jeb800e said:**
> click on "Visual Effects". Now, click on the "None" selection, if not already chosen. Click "Close"

+1

System -> Preferences -> Appearance
set visual effects to none.

This is what I would try first anyway.

---

### Post by jeb800e on 2009-11-14
Did any of these work?

---

