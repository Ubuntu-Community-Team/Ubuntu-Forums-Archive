---
title: "Persistent USB?"
date: 2011-09-21
forum: General Help
---

### Post by PDA1 on 2011-09-21
I have a Ubuntu 10.04 (LIVE) on a USB Stick....it's the one which has the entire system on it and lets you "Try it" before doing an install.  

The problem is, when I use the USB stick and "try" Ubuntu, any changes I make aren't retained.  For example, I have to reinstall Adobe Flash in Firefox everytime I reboot and "Try" Ubuntu again.

How can I get the stick to remember the changes?

---

### Post by patryk77 on 2011-09-21
System / Administration / Startup Disk 

I believe you can get up to 4 GB for saving.

Of course, you will need to use another medium to write to the disk (run it off a CD or an already installed version)

---

### Post by PDA1 on 2011-09-21
I understand the Startup Disk....but I want it exclusively on a USB stick.  How do I do it?  Say, marking a Startup Disk won't create what I want will it?  That makes it unchangeable also...isn't that correct?

---

### Post by patryk77 on 2011-09-21
You can use it exclusively from a USB stick, and the startup disk creator has an option to make it persistent. In the attached screenshot, it's at the bottom (grayed out because I didn't specify the iso or a valid partition)

Set it to "Stored in reserved extra space" and define how much.

You just can't boot from the USB disk, and format the disk while you're running off it.

Though I am not sure if that saves the packages as well, as I haven't used that in ages and there may be another way.

---

### Post by PDA1 on 2011-09-21
Perfect!  It works great!    Thank you.

---

