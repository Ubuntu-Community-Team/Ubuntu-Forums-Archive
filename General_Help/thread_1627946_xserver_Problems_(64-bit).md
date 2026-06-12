---
title: "xserver Problems (64-bit)"
date: 2010-11-22
forum: General Help
---

### Post by Crashedata on 2010-11-22
I bought a new laptop with Win 7 recently, and because I love Ubuntu, I decided I was going to install a dual boot between 10.10 and Win 7 on it. I put in the disc (Ubuntu 10.10 64-bit) in the drive, and it booted into the OS preview fine. I could use everything. After installing however, when I boot into Ubuntu, X fails to start.

The only thing it tells me is (and I am not sure if I am getting this right as I am going off of memory) that there is a problem with the intell-apg or something like that.

Here are the specs of this laptop:

Acer spire 7741Z-5731
Intel Pentium Dual Core P6000 (1.86 GHz, 3MB L3 Cache)
3GB DDR3 RAM
17.3" HD+ LED LCD (Not sure if this matters)
INTEGRATED 1GB Intel HD Graphics
250 GB HDD
HDMI Out (Never use it as all the HDMI ports on my TV are taken)

Not sure if this matters, but according to the manual the optimal resolution for the monitor is 1600 x 900. Does not mention best refresh rate though. Oh, and if I try to manually start x, all that happens is the screen goes blank and I have to force a shut down by holding down the power button.

Any help would be greatly appreciated.

---

### Post by Crashedata on 2010-11-22
Bump

---

### Post by Crashedata on 2010-11-22
UPDATE: It looks like X is trying to start automatically like a minute and a half after I start typing in commands trying to fix it. Problem is, I am not telling it to start, I am not done trying to trouble shoot, so all that happens is I get a black screen that ruins me trying to fix the damn thing. 

Maybe I have to reconfigure X, but I don't remember the command for that.

This is starting to get frustrating. Maybe I should just uninstall it, and just use Win 7.

---

### Post by Crashedata on 2010-11-24
This is solved. I ended up just installing 10.04, and it works great. I tried everything I could think of for 10.10, and even found some troubleshooting steps I found. It turns out there is a bug in 10.10 with newer integrated Intel Chipsets that causes the Intel AGP file not to load, and for the x system to think all entries for Intel are invalid. Some trouble shooting steps I found online were to download all updates (as there was an update to fix this bug), and to delete a file (cant remember its name off the top of my head) and re create it. None of this worked for me, and downloading the update for the Intel stuff did NOT fix the bug.

So, I downgraded to 10.04 and all is fine now. It seems that the bug originates with the install application from the Desktop CD not properly detecting newer Intel chipsets (a bug 10.04 does not have), which causes invalid entries in a X Server file (again cant remember its name off the top of my head). There is a bug report for this all ready that states the bug has been fixed, but apparently that is not correct. In addition, I am NOT sure if this problem is also present with the Alternate Install ISO. Be interesting if someone with similar hardware to mine was willing to try the alternate out and let everyone know.

---

