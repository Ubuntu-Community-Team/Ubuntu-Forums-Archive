---
title: "Desktop Weirdness"
date: 2009-10-31
forum: General Help
---

### Post by gcndavidmn on 2009-10-31
Ok I am relatively new to linux so as 9.1 came out recently I thought Id give it another go! I installed 9.1 fresh on a separate drive in my PC. I currently have 2 monitors plugged in but one is disabled in the preferences. I set up the monitor Im using to use its full native resolution 1920x1080 but when I move my mouse to the right edge of the screen the desktop pans across to reveal a large black section. I dont really understand what is going on here. I installed the nVidia driver for my 260GTX, if that helps.

Regards
Dave

---

### Post by gcndavidmn on 2009-11-01
Update:
I have found what is wrong but I dont know how to solve it. The OS thinks that my screen is 3072x1080 pixels when in fact is it 1920x1080 (I found this in the "Nivida X Server" setting which is what was installed when I installed the driver. What do I do? This is quite annoying!

There is a mode in "X Server Display Configuration" for "Panning" where by default it was set to 1920x1080.

---

### Post by efflandt on 2009-11-01
Normally if you have 1 monitor, your desktop is 2 screens wide and you can pan from one half to the other half.  With 2 monitors maybe the system assumes that your other screen is your other monitor.  But with the other monitor disabled that is blank (black).  What does the symbol show in lower right of screen and is right half of that black?  Or what happens if you set panning to 2 screens wide?

PS: I am just guessing (do not currently have 2 monitors connected).

---

### Post by simpleeddie on 2009-11-01
Hey, I've had the same exact problem today, fresh install of ubuntu 9.10 didnt play nice for a short while, so I had to intervene.

Can you tell me what tool you used to install your nvidia drivers (specifically I want to know if you used EnvyNG), and can you also tell me if you have the Nvidia X Server Settings Application in your Preferences menu?

Also, do not worry, this is an easy problem to solve :)

---

### Post by gcndavidmn on 2009-11-01
I installed the drivers via going into administration and "hardware drivers" and followed that through.

I don't have the application in the preference menu, I get to it via the display display section of the preference menu. When I select it it says "It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?" and I click yes.

PS
Just checked I don't have the latest drivers from nVidia, should I download them? On windows Id do it straight away but on Ubuntu I'm wary because I haven't got a clue.

PPS
Just rebooted and that option is now in the Admin section

---

### Post by gcndavidmn on 2009-11-01
What is this easy solution?

---

