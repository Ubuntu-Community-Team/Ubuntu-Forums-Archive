---
title: "Computer freezes after several hours(?)"
date: 2011-05-29
forum: General Help
---

### Post by earlycj5 on 2011-05-29
I'm usually pretty good at solving these issues after being a Linux user for so long, but this one has me stumped.

I've a new Dell Precision T1500, Core i5, 8gb RAM, nvidia graphics card, that seems to freeze after some hours.  I'm not sure how long exactly, more than two hours at least.

OS: Ubuntu 11.04
Cause: leave computer turned on, unattended for some time >2hrs.
Symptom: Screens are blank, no response to keyboard or mouse input, reboot is only way to rectify.

Things I've tried: [LIST]
[*]Turn off screensaver
[*]Disable "Sync to VBlank"
[*]Disable screen power management, screen stays "on" always
[/LIST]

So far none of these have corrected the issue.  The screens are still on, but there is nothing displayed.  Same thing did happen with Ubuntu 10.10, I'd hoped maybe 11.04 would fix it, alas, no.

---

### Post by linuxinstalledfromhdd on 2011-05-29
Okay. Try with a USB live stick made with "persistance" and use only Ubuntu 10.10 32-bit, and leave your computer booted to that USB stick for more than two hours at least.  Check the logs and make note of anything strange.

---

### Post by earlycj5 on 2011-05-29
> **linuxinstalledfromhdd said:**
> Okay. Try with a USB live stick made with "persistance" and use only Ubuntu 10.10 32-bit, and leave your computer booted to that USB stick for more than two hours at least.  Check the logs and make note of anything strange.

Whoops.  I forgot to ever change my version in my profile and/or add to the post.

Fixed that.

I'm curious, why use 32bit?  Could you elaborate more please, what makes you think it's related to being 64bit?

---

### Post by earlycj5 on 2011-05-31
Anyone have any ideas?

Log files to check?

---

### Post by earlycj5 on 2011-06-30
After digging through log files and finding nothing, custom compiling an upstream kernel (thinking maybe it was a kernel bug) and still having the issue. I ran memtest86+ on the machine last night.

Several errors were indicated.  Pulled out one stick of RAM, testing now to see if I pulled the right one out.

---

### Post by wildmanne39 on 2011-07-01
> **earlycj5 said:**
> After digging through log files and finding nothing, custom compiling an upstream kernel (thinking maybe it was a kernel bug) and still having the issue. I ran memtest86+ on the machine last night.

Several errors were indicated.  Pulled out one stick of RAM, testing now to see if I pulled the right one out.

Hi, let us know if memory fixes your issue.
If not you can have a look at this link.
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

---

### Post by earlycj5 on 2011-07-01
When I last saw it, it was still working fine.

Frankly, I'd be surprised if it were not the RAM, see my previous post regarding Memtest86.

---

