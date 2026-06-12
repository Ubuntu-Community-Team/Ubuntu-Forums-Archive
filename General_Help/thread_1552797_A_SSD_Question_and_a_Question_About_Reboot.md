---
title: "A SSD Question and a Question About Reboot"
date: 2010-08-14
forum: General Help
---

### Post by JosephW90 on 2010-08-14
I am hoping that someone either knows the answer or can point me in the right direction, my head is sort of spinning after countless goggling.

My first question relates to Solid State Drives and Linux. It seems that every article I read on the topic has conflicting advice.  But from the best I can gather, it seems that TRIM, done via discard, in your fstab, and ensuring proper Alignment are important and with current drives in the market it is not necessary to fuss too much over read and write cycles.  

I have an Intel X25-E 32GB SLC SSD with 88560 firmware.  Testing it with hdparm -I  the drive dose not show support for TRIM.  I found a launchpad bug about a lack of TRIM in 10.04, so I built a back ported kernel from 10.10 into a live CD, booted off the live CD and tested again with hdparm -I and I did not find TRIM support, so am I missing something or is it really not there? And if so, how big of a deal is that?  I have read everything from people saying it it a no go at that point to it being not such a big deal.  

If anyone knows more info about this, it would be helpful.  

The second question has to do problems rebooting.  The system will shutdown fine with a halt command, but locks up after given a reboot one.  I have a DP55KG with current firmware (KG5531P 5/21/2010), I found a thread from back in 2009 about someone experiencing the same problem with the board without finding resolution but I have not found anything more recent.  So reboot may be a lost cause, but if anyone had heard anything more recent / concrete about a reboot workaround or fix for the Intel DP55KG motherboard, I would be grateful for the info.  

Thank you =)

---

