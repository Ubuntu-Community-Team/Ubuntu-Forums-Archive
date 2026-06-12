---
title: "Desktop switcher hosed"
date: 2010-11-05
forum: General Help
---

### Post by triplemaya on 2010-11-05
Hi. I managed to mess up my system with mac4lin. Having run the install script, I found I could not get back to the most basic of settings in visual effects. My system is not fast enough to run these effects. It does wobbly windows fine, and the cube, but when I use the window switcher (alt tab) with a lot of firefox windows open, the graphics hangs. Since I spend all day every day swicthing from one window to another, this is unusable.
I uninstalled mac4lin. No difference. Everything back to standard ubuntu, EXCEPT the window switcher.
Finally, in desperation, I did a fresh install. No good. I am still stuck with this situation, and, of course, I still have to install all the software i use!
Please could someone help me get this os working for me again.
Thanks.

---

### Post by sikander3786 on 2010-11-05
Sorry to hear you troubles.

Can you please explain what is the exact problem for now? You reinstalled Ubuntu from scratch, right? And still the desktop switcher is not working?

Or you need help regarding some other topic?

---

### Post by cipherboy_loc on 2010-11-05
If we assume that your issue lies with the desktop switcher, then:

From what I can tell it seems like mac4lin requires the compiz package. This gives you the nice (for people with fast graphics cards) graphics. From a terminal, "sudo apt-get remove compiz" will remove the main source for the different graphics. 




Cipherboy

---

### Post by triplemaya on 2010-11-05
Thanks 

I ran 

sudo apt-get remove compiz

but the situation is unchanged.

With None selected in the Appearance>  Visual Effects setting dialog, the switcher window comes up after about three seconds, and then works reliably. But it's all dead slow. Instead of just the little box with an array of icons, it shows an icon of each window, and each icon is window shaped.
When the Normal setting works, with only one or two windows open, it shows icons of the open windows which are about teh same size, about 1.5 inches high, but these are squarish.

The None setting sometimes shows what looks as if it ought to be the ordinary switcher, with all small icons and text describing the window the switcher is currently on, but one or two of the icons have the 1.5 inch window behind them. Sometimes they are different sizes. When the switcher is working on just a few windows, smaller windows have bigger pictures!?

With the Normal setting, if I have more than a few windows open, the switcher window does not display, even if I hold down alt tab for some time, and when I release, the app may or may not switch to another window.

---

### Post by cipherboy_loc on 2010-11-06
Interesting... Please post the output of lspci | grep -i 'vga'. It might be that your graphics card is slow, or that you need a driver for it.

---

### Post by triplemaya on 2010-11-06
Solved by brute force. Simply ran ubuntu from the disk, copied .gconf to a stick, and copied over the problematic .gconf in my installation, and reinstalled any missing options.

---

### Post by triplemaya on 2010-11-06
Didn't notice your post cipherboy.

$ lspci | grep -i 'vga'
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)

I would have expected this to be pretty standard and a driver to be part of karmic, but if there's any way to improve performance I would love to know about it.

---

