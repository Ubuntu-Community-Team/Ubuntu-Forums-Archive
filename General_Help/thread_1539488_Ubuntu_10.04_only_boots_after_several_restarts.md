---
title: "Ubuntu 10.04 only boots after several restarts"
date: 2010-07-26
forum: General Help
---

### Post by B3r3av3d on 2010-07-26
Hey there,

I really looked around the forums and used google a lot to find a workaround for the following problem but I just wasn't able to find something like it.
I use Linux distributions for sometime now but I would still call me a newby to the OS.

I have Windows 7, Linux Mint and Ubuntu (10.04)[all 32bit] installed on my Laptop (Core2Duo 9700, 4GB DDR3, ATI Mobility Radeon 4650).
Okay so now I will get right to the point:

I start the system. The Grub Loader shows me all the options. I choose Ubuntu (first entry) and then the flash boot screen shows up. But only for a few secs, then it flickers and the screen just turns black. Nothing more happens. (Even if hours pass, and it can't be a only screen issue because there is no jungledrumsound) 
I press and hold the power button so the system shuts down. Then I start again. If I am lucky it perfectly works. If not the same thing happens and I have to try again.

I already checked the hardware. It all works properly. There is no problem when starting W7 but the same problem with Linux Mint.


Any ideas? Thank you!

B3r3av3d

---

### Post by B3r3av3d on 2010-08-11
sorry for the double post but I really try to get this solved and I will be going to university soon and I need a running Linux System on my Laptop.

Is there really no one with a similar problem or any idea?

I found out that I can start the system in recovery mode (but do nothing with it) and then restart the system and it works fine.. but it takes some time. I'm really confused why it only works on a random basis

---

### Post by deusdiabolus on 2010-09-02
I am currently having a similar issue (I have the same graphics card that you have, but my machine is mostly a stock Dell Dimension 4600 otherwise).  My problem is that it loads the blank screen with the flashing cursor, and then sends me to a TTY login.  Another post I found said that sometimes it does this but continues to load if you wait a few moments, so I waited about 3-5 minutes but my only option was to login.  All I had was shell access - I could boot the GUI with 'startx', but once I did there was no Ethernet/Internet and I didn't have my external USB drive.

I'm currently writing this after booting into recovery mode (hold down SHIFT when GRUB starts to load) and using the 'netroot' option and then 'startx'.  That gives me Ethernet/Internet again, but still no USB external.  I'm trying to update to the most recent linux headers (which I have so far been unable to do from the shell) and I'm going to see what happens then.  If this doesn't work, I think I'm going to watch some television and consider less stressful options.

---

