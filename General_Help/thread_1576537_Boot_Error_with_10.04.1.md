---
title: "Boot Error with 10.04.1"
date: 2010-09-17
forum: General Help
---

### Post by Meiori on 2010-09-17
So a few weeks ago, I was using my desktop and saw that there were some upgrades available. I opened the window up and saw that there was a system upgrade. I was using 9.10 and saw 10.04.1, so I figured "Okay, we'll upgrade". I've never had any trouble doing upgrades before, so I had no reason to suspect there would be one now.

As a little background note, up until this point, my entire Ubuntu/Linux experience was fixing a corrupted file and deleting a virus, all through the use of much Googling. At some point during the installation process, I got an error and after acknowledging it, the thing continued to download just fine. 

Apparently, somewhere after that, my girlfriend turned off the computer at the tower. The next time I boot it up, it starts as normal, I see the nice little red 10.04 Ubuntu screen...


And then it kicks me to a black terminal-like window. Having researched the problem as best I could, the best thing I can figure is that there was some error with the video driver.

I've used the following commands, ```
sudo apt-get upgrade
sudo apt-get Update
sudo apt-get dist-upgrade
sudo apt-get install pkg
sudo apt-get purge pkg
sudo apt-get autoremove
sudo apt-get -f install
``` and been rewarded with a whole lot of nothing. Or I should say, a whole lot of something that meant squat to me.

For example, I used dist-upgrade and was given a display page something along the lines of the following;


Reading package lists... Done
Building Dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove, and 0 not upgraded.
1036 not fully installed or removed.


It asks if I want to continue, I hit 'y' and get an eyefull of errors in a flash. At the bottom of the last screenfull, it says "Processing was halted because there were too many errors.

I don't know what more I could/should add. As I said, from my reading, my best uneducated guess says it's the video driver, but I really don't know. And beyond manually typing out error screens (after figuring out how to slow it down), I don't know how I would paste any needed info.

Any help would be VERY appreciated. Stealing the girlfriend's laptop to do my own things is becoming a source of contention between us.

---

### Post by andrewthomas on 2010-09-17
Try

```
sudo dpkg --configure -a
```

---

### Post by Meiori on 2010-09-17
More errors.

"Processing was halted because there were too many errors."

---

### Post by Meiori on 2010-09-20
... Any suggestions?

---

### Post by Rubi1200 on 2010-09-20
What graphics card do you have installed?

And, for the possible bad news, you may have to end up reinstalling especially with so many errors being returned.

But, first things first, the graphics card.

---

### Post by Meiori on 2010-09-20
An NVIDIA Geforce 8800 I believe.

Edit: If I'm reading it right, the VGA compatible controller being the video card, then an nVidia G86 (GeForce 8300)

---

### Post by Rubi1200 on 2010-09-20
Try booting with the nomodeset parameter; at the GRUB menu "e" to edit remove quiet splash add nomodeset and "Ctrl" + "x" to boot.

Let's see where that takes things.

---

### Post by Meiori on 2010-09-20
Doesn't seem to have changed anything. Admittedly, I could be doing something wrong.

Edit: I did it again, figured out where I went wrong, got a LOT of text going through the screen before it kicked me back to the same terminal-like screen, only the font's a bit bigger now and the text starts at the bottom rather than the top.

---

### Post by Rubi1200 on 2010-09-20
Sorry, not sure what to tell you. I hope others have some ideas for this.

If I find something, I will get back to you.

---

### Post by Rubi1200 on 2010-09-21
> **Meiori said:**
> Doesn't seem to have changed anything. Admittedly, I could be doing something wrong.

Edit: I did it again, figured out where I went wrong, got a LOT of text going through the screen before it kicked me back to the same terminal-like screen, only the font's a bit bigger now and the text starts at the bottom rather than the top.
Did the process just stop there? Did you wait a few minutes to see if it would continue?
You might want to consider going back to 9.10 until these issues are resolved (with 10.10 maybe?).

---

### Post by Meiori on 2010-09-26
How would I downgrade to 9.10 with commands?

---

