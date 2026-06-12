---
title: "Help Setting up a RAID system."
date: 2010-11-05
forum: General Help
---

### Post by enseyn on 2010-11-05
Alright, I have never messed around with RAID before, and this is turning into a nightmare. I have read various guides, and just cant seem to get things working. I have tried several different set-ups to no avail. Please help me figure out where I am going wrong.

I have 3 500GB drives that I am setting up on a RAID5 system, the first thing I tried was having 4 partitions on each drive identical (20GB /, 2gb Swap, 250GB /home, and the rest storage). These were set as mb0 through mb3. I kept getting an error with something along the lines of inframs failed to execute some process or another. I can't remember because it was a few days ago. 

After much messing around I gave up and decided to try something different. Only having my /home as RAID5 and having / on 20GB of the first disk, then just keeping a BU on the second. the third i put some swap space and a small section for encrypted data later on. Now GRUB will not load. please let me know what I am missing and what relevant files or outputs I need to post to help get to the bottom of this.

oh, and I am installing 10.10 if that helps.

Here is a run down of the process I used. I set up the drives initially with the disk utility off the live CD. I then installed mdadm and ran the command:
```
sudo mdadm --create --verbose /dev/md0 --level=5 --raid-devices=3 /dev/sdb2 /dev/sdc2 /dev/sdd3
```
This synced up my /home partitions and the array seemed to be running fine. I then installed ubuntu using the graphical installer and did not run into any problems. Upon restarting i just get a screen that says grub failed to load. I tried reinstalling grub, and it looks like everything is set up right, but again, it fails to load on restart.

---

