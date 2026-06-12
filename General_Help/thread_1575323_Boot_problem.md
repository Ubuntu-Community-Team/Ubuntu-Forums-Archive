---
title: "Boot problem"
date: 2010-09-15
forum: General Help
---

### Post by Benbow on 2010-09-15
I am having serious problems booting up my pc. I am using 10.04 and have been using Ubuntu in its various forms for three years without "serious" difficulties.

Out of the blue my pc refused to boot up with the "error 15" message. I dual boot so I then tried to boot XP - same message. I then went back to Ubuntu and it booted. Since then, 2 days ago, booting up has been erratic with both Ununtu and Windows and the pc is now virtually unusable. I had, just once , the following error message -

"MP-Bios bug, 8254 timer not connected to 10-APIC.
Kernel panic - not syncing : 10-APC + timer doesn't work."

After 24 hours of struggling, it has finally booted up but I am now afraid to turn it off in case it doesn't boot again.

Incidentally, I tried Super Grub and booting with my original 10.04 cd but that wouldn't run either.In desperation I have tried to re install Ubuntu but I can't do that either.

I will be grateful for any help but not too technical if it can be avoided. 

**Sorry, I forgot to mention that I can boot into safe mode with XP but that is all**

Brian

---

### Post by Smart Viking on 2010-09-15
This _might_ be a harddrive issue, do you have any leftover hard disks that you can test?

Try to unplug the hard disk, and then try to boot from the CD, once i had this problem where it would boot from CD if not the harddrive was unconnected, since the hard drive was broken, have no idea why though. :)

---

### Post by TitanusEramius on 2010-09-15
Have you tried to boot on a older kernel to se if that helps?

Try to read this:
[http://www.linuxquestions.org/questions/linux-kernel-70/kernel-panic-not-syncing-io-apic-timer-dosent-work-558748/](http://www.linuxquestions.org/questions/linux-kernel-70/kernel-panic-not-syncing-io-apic-timer-dosent-work-558748/)


As i suspect it might be a recent kernel update there is causing this problem.

---

### Post by Benbow on 2010-09-15
Thanks for your reply. I have tried a spare harddrive without success. 

Brian

---

### Post by wilee-nilee on 2010-09-15
> **Benbow said:**
> Thanks for your reply. I have tried a spare harddrive without success. 

Brian

If you can only boot MS in safe mode then you might check with gparted in Ubuntu to see if the ntfs partitions have any flags. Gparted has to be installed in a installed Ubuntu, but it is on the live cd.

Random booting not booting is a tough one for me. It might help to include the boot script in a response to see the system better, post it in code tags as described in my signature and use the link there to download the script to run it.

---

### Post by Benbow on 2010-09-15
Hi TitanusEramius

I tried your link but your blog is not available could you post it here or pm it to me please.
Brian

---

### Post by wilee-nilee on 2010-09-15
> **Benbow said:**
> Hi TitanusEramius

**I tried your link but your blog is not available could you post it here or pm it to me please.**
Brian

Not sure who your talking to here, if your referring to the bootscript click on the words bootscript in my sig.

---

### Post by oldfred on 2010-09-15
A quick google search shows the same problem back in 2006 with nvidia drivers. Not sure if this is the same or not.

One suggest was noapic, so try  using e on the grub menu and replace quiet splash with noapic.

Did you change or update video drivers?

---

