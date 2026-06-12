---
title: "Resize partitions after installation?"
date: 2011-09-13
forum: General Help
---

### Post by stargazer_010 on 2011-09-13
I'm running Ultimate from an external hard drive and basically just need to  know if i can adjust my partitions without losing what I have set up already (just want to make the partition for ultimate larger; there is plenty of space on the drive).  I've looked in the Disk Utility app, but I'm not sure what to do in there with adjustment, if I can do anything at all.

I have browsed through the forum here and found advice/etc. about partitioning before installation or during installation, so if I've missed a thread about this subject, I apologize.

Any help would be much appreciated.

---

### Post by WorMzy on 2011-09-13
Generally, you can resize partitions without issue. However, you can't resize partitions which are in use, so you'll need to either boot into another Linux partition, or boot up a LiveCD/USB before you can resize the partition in question.

Make sure to back up any important documents before hand, just in case something goes wrong (power-outage, application crash, user-error, etc).

---

### Post by drs305 on 2011-09-13
You can use Gparted to resize the partition, however the partition must be unmounted while the operation is performed. You can use an Ubuntu partition to perform the operation. From the LiveCD, before starting the operation, you will also have to unmount the 'swap' partition.

There are various guides floating around showing how to accomplish this. I had a thread on expanding /, which should give you some pertinent information.
[http://ubuntuforums.org/showthread.php?t=1219270]("http://ubuntuforums.org/showthread.php?t=1219270")
Also see *srs5694's* link on that page.


Don't forget to backup important data.

---

### Post by rhapa on 2011-09-13
> **WorMzy said:**
> Generally, you can resize partitions without issue. However, you can't resize partitions which are in use, so you'll need to either boot into another Linux partition, or boot up a LiveCD/USB before you can resize the partition in question.

Make sure to back up any important documents before hand, just in case something goes wrong (power-outage, application crash, user-error, etc).

Well, here I resized the currently partition with gparted with no problem at all. It just ask to reboot the computer to complete the task and once reboot the partition was resized (just like an Windows application would do). 

I also resized the partition with a live cd and it worked as great as the other way, but way smoother. When I rebooted the computer the system just scanned the HD to update the settings.

---

### Post by stargazer_010 on 2011-09-15
Thanks so much, that was exactly the info I needed.  :D

---

### Post by stargazer_010 on 2011-09-15
I ran gparted from my live disk and it won't show the external drive that I have Ultimate installed on.  When I checked my Disk Utility (from the live disk) and try to do anything to the external it says "Daemon is inhibited."  Any suggestions there?

BTW, your detailed write up in the forum was most excellent and very informative.  Thank you for directing me there.

---

### Post by stargazer_010 on 2011-09-19
Please disregard my last message.  Got it all worked out.  Just had some operator error going on.. lol

---

