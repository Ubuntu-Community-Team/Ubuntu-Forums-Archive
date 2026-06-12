---
title: "Simple monitor brightness/gamma adjustment"
date: 2009-07-25
forum: General Help
---

### Post by JamesRead on 2009-07-25
This is my first post I do hope someone can help.
 
I have been using Ubuntu now for a couple of days and find it very good, some of it the image viewer for instance is a bit slow but never mind :-)
 
There is a little application I use in Windows though that doesn't appear to be available for Ubuntu. Its called Gamma Panel and can be downloaded here: [http://majorgeeks.com/Gamma_Panel_d2796.html](http://majorgeeks.com/Gamma_Panel_d2796.html)
 
I use it for the photographs I have printed by Photobox, I sent a trial pic to be printed and it came back far too dark, they also sent me a print of their Calibration pic.
 
Comparing the two, the Calibtation pic on screen was too light and this is where Gamma Panel comes in useful I can alter the monitor brightness and Gamma with the program AND save the setting and alter it with a click.
 
It means for instance that I can have one pic for Photobox and another for a website in the space of a few seconds.
 
I have been down the ICC profile road and am not interested in paying loads of money for something that is only usable for 1 printer setting, 1 type of ink and 1 type of paper!
 
I found out that I didn't need a calibration device or ICC profiles, the prints I get from Photobox are perfectly adequate. Gamma Panel (please take a look at it) or something very similar is all I need, it is simple easy to use and does the job to my satisfaction and no doubt to the satisfaction of the 45,000 other people who use it.
 
I also think that the law of diminishing returns steps in here a simple application will alter things by 90% anything else may be better but only by a few points more.
 
James

---

### Post by JamesRead on 2009-07-25
Bump

---

### Post by CatKiller on 2009-07-25
For simple RGB gamma adjustments, you can use xgamma. Once you've found values you're happy with, you can add those values to your xorg.conf to have them applied automatically when X starts. For colour profile application you can use xcalib.

You seem to have misinterpreted what colour profiles are for, and how much they cost (they are free, generally, either provided by the device manufacturer or calibrated yourself). They don't mean that you can only use one display device; quite the opposite. Without using colour profiles you can only use what you use. Your images will look wrong on anything else. If you use colour profiles you can see the same image in the same way in whichever device or medium. They are a means for allowing for the differences in display characteristics in different devices and media. Properly applied colour management means that you will always get the image as it was intended, not munged by whatever flaws exist in the technology.

---

### Post by JamesRead on 2009-07-26
Dear CK,
 
Gamma Panel does all I need with one click or indeed one key stroke.
 
Its so esy to use its quite frankly ridiculous.
 
James

---

