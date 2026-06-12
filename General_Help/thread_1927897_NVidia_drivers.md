---
title: "NVidia drivers"
date: 2012-02-19
forum: General Help
---

### Post by layers on 2012-02-19
I used to have everything sorted out, until I booted with a Windows CD, just to see something. That messed up my grub menu and my drivers.

The boot menu was not so bad to revive - it's the drivers I'm having trouble with. The laptop had NVidia M310, so I went to root shell and installed the NVidia script provided from their website. Now, at each boot up it doesn't work. So in orde rto get a normail screen with proper resolution, I need to click restart X, but the colors are still bad, and when I run the NVidia settings, it tells me to update the X configuration, and even when I run it, it is the same thing on the next bootup. How can I make the drivers love me again?

---

### Post by layers on 2012-02-19
.

---

### Post by gordintoronto on 2012-02-19
So you ran: sudo nvidia-xconfig

You have Ubuntu 11.10, on what brand and model of computer?

Did you run Additional Drivers?

---

### Post by pqwoerituytrueiwoq on 2012-02-19
you may need to run [FONT=Courier New]nomodeset[/FONT] on your kernel's boot line
i forget where the file is but 
[FONT=Courier New]locate grub.cfg[/FONT] will tell you where it is 
edit the file find the line with [FONT=Courier New]quiet splash[/FONT] on it and add [FONT=Courier New]nomodeset[/FONT] to the line in side the quotes
...[FONT=Courier New]"quiet splash nomodeset"[/FONT]

---

### Post by layers on 2012-02-21
yeah, I needed to blacklist the neuveau drivers

---

