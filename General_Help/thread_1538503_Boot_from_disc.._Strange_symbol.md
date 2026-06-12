---
title: "Boot from disc.. Strange symbol"
date: 2010-07-25
forum: General Help
---

### Post by .Griff. on 2010-07-25
Hi peeps,

New to Ubuntu so go easy on me. I've inherited an old laptop, a Fujitsu Siemens Amilo Pro V100 to be exact which I've upgraded to 1gb of memory. 

Windows XP and Windows 7 installed fine and ran ok'ish but obviously the laptop wasn't what you'd call speedy. As a result I thought I'd give Linux/Ubuntu a go and downloaded the ISO and burned the image to disc.

When I boot from the disc it very briefly display "ISOLINUX 3.xx Debian ... Copyright 2008" or something like that at the top of the screen and then the laptop screen displays a weird symbol and stays like that permanently.

[http://img.photobucket.com/albums/v427/griff_90/d9c03dfb.jpg](http://img.photobucket.com/albums/v427/griff_90/d9c03dfb.jpg)

It's a bit hard to make out in the picture but it's something in a rectangle = and then a man in a circle. Not sure if that's something to do with Ubuntu or the laptop.

Any idea's and/or suggestions?

---

### Post by TeoBigusGeekus on 2010-07-25
When you see these "symbols" press any key quickly.

---

### Post by FresnoFightFan on 2010-07-25
> **.Griff. said:**
> 

Any idea's and/or suggestions?

maybe your ISO image is bad. when i boot my Ubuntu from my Flash drive on other peoples computers, it shows  the same thing but boots strait threw. now that i got it on a HDD and don't need to boot from the flash, it doesn't show it anymore.  when the image pops up again, try pressing the same key you would to get to the BIOS.  hopefully thers a menu that might pop up for you to mess with or maybe the list of Kernals you can choose from.

---

### Post by Schrute Farms on 2010-07-25
I had the same thing happen when trying to install 10.04 on my old desktop.  When I pressed a key, it did go a little farther, but not far enough.  I could never install off of this disc on this desktop, not even the live CD would work.  (The disc is fine, it worked on my laptop).  I ended up downloading 9.10 then used update manager to upgrade to 10.04; the computer didn't work correctly after the upgrade.  I ended up reinstalling 9.10 and sticking with it.

Long story short, if pressing a key still doesn't get you anywhere, maybe the laptop just doesn't like 10.04.  Try one of the other versions instead.

---

### Post by theozzlives on 2010-07-25
> **Schrute Farms said:**
> I had the same thing happen when trying to install 10.04 on my old desktop.  When I pressed a key, it did go a little farther, but not far enough.  I could never install off of this disc on this desktop, not even the live CD would work.  (The disc is fine, it worked on my laptop).  I ended up downloading 9.10 then used update manager to upgrade to 10.04; the computer didn't work correctly after the upgrade.  I ended up reinstalling 9.10 and sticking with it.

Long story short, if pressing a key still doesn't get you anywhere, maybe the laptop just doesn't like 10.04.  Try one of the other versions instead.

Never ran into that problem, but have seen that screen. 9.10 is buggy, I'd follow the advice above and press a key. Also run a md5sum on the ISO.

---

### Post by ThomasHC on 2010-07-25
> **.Griff. said:**
> Hi peeps,

New to Ubuntu so go easy on me. I've inherited an old laptop, a Fujitsu Siemens Amilo Pro V100 to be exact which I've upgraded to 1gb of memory. 

Windows XP and Windows 7 installed fine and ran ok'ish but obviously the laptop wasn't what you'd call speedy. As a result I thought I'd give Linux/Ubuntu a go and downloaded the ISO and burned the image to disc.

When I boot from the disc it very briefly display "ISOLINUX 3.xx Debian ... Copyright 2008" or something like that at the top of the screen and then the laptop screen displays a weird symbol and stays like that permanently.

[http://img.photobucket.com/albums/v427/griff_90/d9c03dfb.jpg](http://img.photobucket.com/albums/v427/griff_90/d9c03dfb.jpg)

It's a bit hard to make out in the picture but it's something in a rectangle = and then a man in a circle. Not sure if that's something to do with Ubuntu or the laptop.

Any idea's and/or suggestions?

Hmm, that symbol is supposed to be there, but not permanently, that's rather odd. How long have you waited?

If it continues to misbehave, I would download the alternative CD iso image, burn it to a CD-R and continue from there. What the alternative CD is, is a disc tailored for computers that have trouble with the live system, or are much to slow to run the live system. It's basically an installer disc without a live session and a fairly straightforward interface. You can find it poking around on the download page.

Best of luck!

Thomas

---

