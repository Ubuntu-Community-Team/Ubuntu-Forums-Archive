---
title: "Black Screen at install still an issue"
date: 2010-06-13
forum: General Help
---

### Post by Syncvoid on 2010-06-13
Hello all:

I've been having trouble with this for about a week. When trying to install the latest Ubuntu it goes to black after the flash screen. From what I have read this is due to my video card drivers. I have spent some time looking at trying to switch the setting with:

i915.modeset=1 (or 0) 

But I can't seem to get that far. I am booting from a USB and I get to the install screen. When I click "Install to disk" it starts the process and eventually it all goes black and I can't see a thing. At some point I understand I should be hitting F6 to pull up a command prompt and get through installations, than I can make the change permanent once I get it on the drive, but I am still stuck trying to get this to switch modes. 

I don't know if I am reading the guide wrong or what.

Can some one give a Ubuntu noob help. I am using HD5770.

Thanks,

Sync

---

### Post by dino99 on 2010-06-13
boot without "quiet splash" to see comments

you can try with different parameters: nomodeset, irqpoll, acpi=off, lapic=off, apic=off

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

