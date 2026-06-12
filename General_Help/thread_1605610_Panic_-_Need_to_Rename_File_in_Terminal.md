---
title: "Panic - Need to Rename File in Terminal"
date: 2010-10-25
forum: General Help
---

### Post by Quarkrad on 2010-10-25
I made a change to fstab and now my 10.10 system will not boot.  Fortunately I made a copy before I made the change so I now need to go to /etc/ and change fstabold back to fstab.  I booted with a live CD and via terminal went gksudo nautilus to make the change but I could not find/nagivate to the original systems /etc/ folder.  So I rebooted and choose recovery mode and booted to command prompt.  I cd'd to my /etc/ folder and can see fstab and fstabold.  I'm not familiar with terminal commands (newbie) but I keep getting an error.  To see if I could change a file name I tried to change fstabold to fstabx.  (I would then change fstabx to fstab as this is my original fstab file).  Problem is I keep getting **Bareword "fstabold" not allowed while "strict subs" in use at (eval 1) line 1**.  How do I change file name so I can get my system back?  I would like to rename the current fstab file to fstabdump and then change fstabold to fstab.

---

### Post by ezsit on 2010-10-25
When you are in a terminal and you are in the /etc directory, cp is the command to use to rename (and copy)

**cp fstab fstabdump**  (copy fstab to fstabdump)
**rm fstab**            (delete fstab)
**cp fstabold fstab**  (copy fstabbodl to fstab)

---

### Post by Quarkrad on 2010-10-25
ezsit - you have saved my life!  Many thanks - system up and running.

---

### Post by ezsit on 2010-10-26
Glad I could help. Happy trails. :-)

---

