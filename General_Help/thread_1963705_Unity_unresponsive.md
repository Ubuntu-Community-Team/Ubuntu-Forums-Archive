---
title: "Unity unresponsive"
date: 2012-04-22
forum: General Help
---

### Post by gsarrica on 2012-04-22
When I login using the normal Unity desktop it seems to lock up. When I let it sit I am able to open the terminal. (which opens very slowly) once open the terminal seems to respond normally. If I try to move a window, or interact with the desktop with my mouse it starts responding extremely slow. 

I can check "top" and nothing is using the cpu. I have tried reinstalling compiz and unbuntu-desktop with the purge command to remove configs and the same issue happens. 

I have also tried to kill compiz and nautilus with no improvement. The only thing that works is running unity 2d.

All users on my machine are affected by this, making a new user did not help.

I also decided to try to upgrade to 12.04 to see if it would clear things up but no luck.

It seems like it is an issue with composition but I cant seem to put my finger on it. 

I have an nvidia card with the proprietary drivers installed. (I also re-installed these)

Does anyone have any other ideas?

Thanks for the help in advance!

---

### Post by jerrrys on 2012-04-22
Have enough RAM?

Next time it happens, [open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal") and enter:

free -m

That will tell you if your using SWAP (which would slow you down).

---

### Post by gsarrica on 2012-04-22
> **jerrrys said:**
> Have enough RAM?

Next time it happens, [open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal") and enter:

free -m

That will tell you if your using SWAP (which would slow you down).

So I have seemed to fix it. It was the Nvidia Driver. I went back 1 version and all is good. I should have mentioned I had been running normal Unity (3d) for years. I have 6 GB ram. 

For others: first download the older nvidia driver from nvidia.com

Uninstall nvidia-current

reboot to recovery mode

as root run the downloaded nvidia installer

reboot.  

Things should be back to normal. Not sure if this is a bug or not. I guess I will hang out on the version of the driver for awhile. BTW I have a Nvidia Geforce 8800 GTS.

The version that was broken was 295.40 of the Nvidia driver.

I rolled back to: 295.33

Thanks for the help!

---

### Post by jerrrys on 2012-04-22
Good show and welcome to the forum :)

---

