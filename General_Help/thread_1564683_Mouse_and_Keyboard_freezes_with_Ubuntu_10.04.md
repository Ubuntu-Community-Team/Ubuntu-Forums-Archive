---
title: "Mouse and Keyboard freezes with Ubuntu 10.04"
date: 2010-08-30
forum: General Help
---

### Post by soundandfury on 2010-08-30
So I recently installed Ubuntu 10.04 alongside Windows XP on my computer. Since day 1 I've been having an issue with my Ubuntu partition where after a seemingly random period of time my mouse and keyboard freeze up completely. I then have to turn off my computer from the button on the tower. At first I thought it might be a video card issue. However after downloading all the drivers for my video the problem contnued. I then installed mdetect. This also did nothing. Finally this afternoon I set up computer so that the pointer could be controlled by my keypad (at this point I didn't know the keyboard froze up as well). This of course did nothing. I'm out of ideas and I don't have the Ubuntu  know-how to handle this on my own. Please someone help me.

---

### Post by UtahApocalypse on 2010-09-02
I am having this same issue and hope someone can help.

---

### Post by pmalvr on 2010-09-04
I have the same problem. When I login my mouse stops completely. 

Can someone help?

---

### Post by pmalvr on 2010-09-04
> **pmalvr said:**
> I have the same problem. When I login my mouse stops completely. 

Can someone help?

Well,

After a long search I made, I found a workaround that for now does the job.

Here it is:

Edit **/etc/default/grub**, go to the line that begins like:
**GRUB_CMDLINE_LINUX_DEFAULT=**

Change it to:
**GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off"**

After that, run this command:
**sudo update-grub** 

**Reboot** and that's it. 

The only thing I noticed is that the PC doesn't shutdown by itself completely, I have to press the button to shut it down.

I hope this bug can became fixed in the next builds.

---

### Post by nitindb on 2010-09-21
This seemed to have resolved the issue but after a couple of days I again find my mouse and keyboard freezing. I also find that my parallel port printer had also stopped working.

I tried attaching the output for dmesg and also my syslog but it appears to be too large.

---

