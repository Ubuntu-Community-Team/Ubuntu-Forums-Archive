---
title: "Zotac Ion nearly but not quite shutting down fully"
date: 2009-08-18
forum: General Help
---

### Post by wilbobob on 2009-08-18
When I first connect the mains power to my Zotac Ion mini itx-B-E box it has a steady blue light around the power button. I press the button, the computer starts (Ubuntu 9.04) and the blue light goes out. A red light shows hard drive activity. Everything works fine but when I shut down the blue light flashes, as if in hibernate mode. I intend using this box to stream video to my TV and when it's not in use the flashing light will drive me crazy.
So far I've tried (one at a time) disconnecting the network before shut down; I've modified the Grub boot kernel to add acpi=force and add apm=on; I've installed the code to shutdown with apm instead of acpi; I've tried shutdown -h now and halt -p now. All result in what appears to be a complete shutdown, but the blue light still flashes. 
Is it only me that is bugged by this? Is there anything else I can try? Is it a feature of the Ion motherboard that I'll have to accept, and just pull the plug after shutting down?
Any advice will be gratefully received, but as I'm very new to this my responses may be delayed by thinking time. Apologies in advance

---

### Post by wilbobob on 2009-09-21
Just to close this thread - After working my way through BIOS settings as well I contacted Technical help at Zotac with all the information I had. They advised I should send the board back to my supplier if under warranty. I'm waiting for the replacement now. I think that if it shows the same problem I'm going to disconnect the blue light and forget about it.

---

### Post by Slither2007 on 2009-10-06
I had a similar issue and found I had just put the led on the pins the wrong way (wrong polarity).

---

### Post by wilbobob on 2009-10-09
Fantastic! that worked for me too. I won't pull out the rest of my hair now. I didn't consider the led connection as I believed that if it was the wrong way round it wouldn't work at all. Thanks for posting the solution.

---

