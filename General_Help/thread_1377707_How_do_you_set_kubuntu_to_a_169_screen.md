---
title: "How do you set kubuntu to a 16:9 screen?"
date: 2010-01-10
forum: General Help
---

### Post by Cotopaxi on 2010-01-10
I gave my son, as a Christmas gift, a 16:9 monitor. The problem is that he sees the image as a 4:3 image, extended laterally and totally unreadable.

I have no possibility of adjusting the screen to a 4:3 size. Is there any way to adjust the system settings to a 16:9 screen?

Thanks for your help!

---

### Post by Cotopaxi on 2010-01-10
Is there any trick to set the screen resolution manually?

---

### Post by Cotopaxi on 2010-01-10
How would you do it in Ubuntu?

---

### Post by Cotopaxi on 2010-01-10
bump ;)

---

### Post by lyall on 2010-01-10
> **Cotopaxi said:**
> I gave my son, as a Christmas gift, a 16:9 monitor. The problem is that he sees the image as a 4:3 image, extended laterally and totally unreadable.

I have no possibility of adjusting the screen to a 4:3 size. Is there any way to adjust the system settings to a 16:9 screen?

Thanks for your help!

see the following link about pixel 
[http://www.fourmilab.ch/documents/howmanydots/]("http://www.fourmilab.ch/documents/howmanydots/")

It should help you.
open System > Preferences > Display
if you have a Nvidia card installed at this time select NO at the prompt
then click on Resolution, it will show you the different setting
1280 x 1024 (5:4)
1360 x 768 (16:9)
1400 x 1050 (4:3)

if you open the Nvidia setting and select X servier Display Configuration
you will not see the ratios for the different Resolutions.

good luck and have fun learning

---

### Post by lykwydchykyn on 2010-01-10
Hit alt-f2 and run krandrtray.  It will create a tray icon that will allow you to adjust the display size.  If it doesn't offer you any 16:9 resolutions, either your graphics card isn't configured right or it isn't capable of 16:9 resolutions.

Do you know what the graphics card/chip is?

---

### Post by Cotopaxi on 2010-01-11
Thanks for your two replies, it looks like &#8220;lykwydchykyn&#8221; is correct: My graphics card either is not configured properly or it does not support 16:9 resolutions.

I will have to check my card. Is there any tool in linux, that lists installed hardware ?

Thanks again for your help!

---

### Post by lykwydchykyn on 2010-01-11
> **Cotopaxi said:**
> Thanks for your two replies, it looks like “lykwydchykyn” is correct: My graphics card either is not configured properly or it does not support 16:9 resolutions.

I will have to check my card. Is there any tool in linux, that lists installed hardware ?

Thanks again for your help!

Several.  The most straightforward and useful way to get what you need would be top open Konsole and do this:

```

lspci |grep -i vga

```

Paste the output and we can figure out what needs to be done.

---

### Post by Cotopaxi on 2010-01-14
Sorry I did not reply earlier, but yesterday I "killed" my sons system, I removed xorg and could only boot into console command mode!

So I have been bussy the whole night, fixing the system up again, Today I will follo lykwy*.* ;) isntruction and post the output of:

> lspci |grep -i vga

Thanks again for your help!

---

### Post by efflandt on 2010-01-14
One issue if connected with VGA is that X might not really know what resolutions the monitor is capable of.  For example when an older 1280x720 LCD was connected by VGA, System > Preferences > Display in gnome only listed a bunch of 4:3 modes and the only 16:9 mode it offered was 1366x768 (common for many 720p HDTV displays), which surprisingly worked in X, even though that mode is not listed in any documentation for the LCD (27" Apex HDTV Ready).

When I connected it with DVI to another computer (while in suspend), it was the previous 1280x1024 stretched from previous monitor, but after logging out of X and logging back in, X automatically recognized its native 1280x720.  However, when I booted later, I found that it would not boot due unless I disabled splash, because usplash apparently doesn't even try any resolution other than is listed in /etc/usplash.conf that is not the native resolution of a digitally connected monitor (even if the monitor is capable of the listed resolution).  Once I changed /etc/usplash.conf from:

xres=1280
yres=1024

from previous monitor (which current display could have done) to:

xres=1280
yres=720

Then I was able to re-enable splash with the DVI connected display, everything booted fine, and X automatically used the native 1280x720.

---

### Post by Saiko Berry on 2010-01-14
> **Cotopaxi said:**
> Sorry I did not reply earlier, but yesterday I "killed" my sons system, I removed xorg and could only boot into console command mode!

So I have been bussy the whole night, fixing the system up again, Today I will follo lykwy*.* ;) isntruction and post the output of:



Thanks again for your help!

Well serves you right for deleting Ubuntu's system32 >_>

Anyways, it should be directly selectable inside your graphic card properties. If youre using a new monitor you might also want to make sure you have SINGLE MONITOR selected and not dual screen or laptop monitor or whatever might have been selected instead. If you use ATI, nvidia, radeon etc.. it'll all be in your graphic config gui.

---

### Post by Cotopaxi on 2010-01-16
Sorry for my late reply, the output of:

> lspci |grep -i vga

is:

> 04:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 SE] (rev a1)


Thanks again for your help! :D

---

### Post by lykwydchykyn on 2010-01-16
I'm guessing you don't have the proprietary nvidia drivers loaded then, because that card ought to be capable of some decent resolutions.

Check the hardware drivers tool under the System menu.  See if the proprietary graphics driver is enabled or not.

---

