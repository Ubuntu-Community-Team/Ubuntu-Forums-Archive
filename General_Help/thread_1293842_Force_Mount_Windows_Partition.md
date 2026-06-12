---
title: "Force Mount Windows Partition"
date: 2009-10-17
forum: General Help
---

### Post by lucastang on 2009-10-17
I just recently installed Ubuntu as a Windows Partition, but for some reason my windows files haven't mounted. Has anybody got any ideas how I am able to force mount my windows files and access them? The problem may come from the Wubi.

---

### Post by Gizenshya on 2009-10-17
haven't mounted or won't mount?
if they just haven't mounted go to Places->Computer.  Then right-click on the drive/partition in question and click mount.

If it won't, and it gives you an error post it.  But if there is an error it is most likely that the windows $logfile didn't confirm shutdown of the drive, and you'll have to force mount it.  But all you have to do in that case is click "more info" (or something like that) and type exactly what it shows you into a terminal to override the $logfile and force mount the drive.

Alternatively, if you get that error and are more patient, you can boot into windows and properly shut down the computer, and that will make windows clear the $logfile.

---

