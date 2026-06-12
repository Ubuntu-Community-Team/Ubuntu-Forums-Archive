---
title: "Ubuntu 9.10 LiveCD fails - no luck w/ boot options"
date: 2009-10-31
forum: General Help
---

### Post by Maximus559 on 2009-10-31
Hi! I'm new to these forums, and I'm hoping that someone will be able to help me get Ubuntu 9.10 working. My situation is as follows: I recently downloaded the ISO and burnt it onto a CD-R, and am now attempting to run a LiveCD session on my old Dell Dimension 4500 (1.8 Ghz P4, 512 Mb RAM, GeForce MX420). I know this machine to be fully functional, as it runs both Windows 98 and Damn Small Linux without problems. However, it seems to be having issues with Ubuntu. The CD boots as expected, but when I select the option for a LiveCD session, it goes into the Ubuntu logo screen and hangs there indefinitely. If I hit F6 and delete the "quiet splash --" parameter, I find that it typically hangs somewhere around "* Setting preliminary keymap" or "* Starting early crypto disks". These results are variable - it's gotten as far as something about console fonts, but the system never actually starts up. I tried the standard boot options (noapic, acpi=off, etc) but none of them seem to make any difference. Just for fun, I tried the check CD option in the boot menu, and it checked out fine. Anybody have any idea what the problem is?

---

### Post by nikgare on 2009-10-31
Try the Alternate cd, that might help.

---

### Post by sdpiowa on 2009-10-31
I would also recommend trying the alternate CD for installation.

---

### Post by P4man on 2009-10-31
I had the same.. hung at "Starting early crypto disks" trying to boot from usb stick. Running the "check the cd for errors" showed no errors. Yet when I tried with another USB stick, it booted just fine.

---

### Post by Maximus559 on 2009-10-31
Will this alternate install CD allow me to start a LiveCD session? I'm not looking to install just yet, as it may be that even an HD install would have the same error, and would therefore be a waste of time. 

I've been reading about some kind of disk image verification program (something to do with "hash") that is recommended in situations like this. However, since my CD passed the self-check program, I'm assuming that this is unnecessary. Is it? Also, would burning the ISO onto a new CD, possibly from a different manufacturer, have any chance of correcting this problem in the way that P4man's second flash drive did?

---

### Post by P4man on 2009-10-31
> **Maximus559 said:**
> Will this alternate install CD allow me to start a LiveCD session? 

No.

> I've been reading about some kind of disk image verification program (something to do with "hash") that is recommended in situations like this. 

MD5 checksum. But if you're somehow suffering the same as me. it wont help. It verifies the downloaded iso, but if the cd verification doesnt give an error then your iso was fine. It basically does the same MD5 check.

> Also, would burning the ISO onto a new CD, possibly from a different manufacturer, have any chance of correcting this problem in the way that P4man's second flash drive did?

Possibly. Would be interesting to find out. If it does help than I have no sensible explanation for it, then again i dont have such explanation for what happened with my stick.

 Alternatively you could try making a bootable live usb stick, assuming the machine can boot from usb. You can make a stick easily with [unetbootin]("http://unetbootin.sourceforge.net/")

---

### Post by Maximus559 on 2009-10-31
Thanks for the replies. I've confirmed now that the CD is fine, as it ran a perfectly normal LiveCD session on a Compaq Presario V2000 laptop that I tried it out on. The task now would appear to be purely system-specific troubleshooting. Earlier, I read a post from someone who had a similar problem, which was corrected by removing a piece of hardware (the graphics card, I believe). Could a specific piece of hardware be causing this problem? For reference, the machine I'm working on currently has the following pieces of hardware installed: Lite-On CD-ROM, Samsung CD-ROM, generic floppy, 8 Gb HD (Western Digital I think), GeForce MX420, SoundBlaster PCI 128, TRENDnet wireless adapter (PCI), and a generic PCI USB board. Any of these look like suspects?

---

### Post by Maximus559 on 2009-10-31
Update: I removed every PCI device listed above, and Ubuntu booted perfectly. Now to add things back in one by one and see what the problem is...

---

### Post by Maximus559 on 2009-11-01
Okay, it was the TRENDnet PCI wireless adapter. Guess I'll have to find a different one. Strange that such a benign piece of hardware should be the cause of a total startup failure.

---

