---
title: "Ubuntu 11.04 Failed to Boot Completely (no display)"
date: 2011-06-25
forum: General Help
---

### Post by Kentucky88 on 2011-06-25
I have been using Ubuntu 11.04 since about the time it released with no problems until a couple days ago.  I started my computer and saw Ubuntu flash through the purple screen while booting, but then the display just went blank.  I still saw hard drive activity and after a few minutes, the heatsink fan started running louder as it usually does since I am running a distributed computing application that puts the CPU under full load.  After a few more minutes of black screen, I hit the reset button and the system booted fine.  That happened again this morning, except only after the 3rd attempt was I able to get into my desktop.  I backed up all my important files, but I am afraid to turn off my computer in case this is the last time I will be able to log into Ubuntu.  I was experimenting with overclocking settings and my system was unstable last week, but I found stable settings and it no longer freezes / crashes.  I'm worried that I corrupted some files while the system was unstable and crashed.  Once I boot however, the system is stable and does not crash.  I suspect that maybe the issue is with the nVidia graphics driver that I am using (running nVidia Geforce 210 card).  I say this because sometimes small black rectangles will appear on my desktop, but they go away once I move a window over them...a small annoyance, figured it was driver quality issue.  What should I do?  Is there a way to do a file check on all system files?

---

### Post by oldfred on 2011-06-25
You can use this to check that hard drive sees all data ok. Run on all Linux ext3 or ext4 partitions.

#From liveCD so everything is unmounted,swap off if necessary, change sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors:
sudo e2fsck -f -y -v /dev/sdb1

You could also force a reinstall of the nVidia drivers - nvidia-current nvidia-settings in synaptic and then run this to see if some setting is out of place.
sudo nvidia-xconfig

---

