---
title: "can't install multi-disk app in wine"
date: 2009-07-19
forum: General Help
---

### Post by nephish on 2009-07-19
hey all, 

i have a game that came in 4 cdroms, the difficulty that i am having is when the windows installer asked for disk 2, i could not eject disk 1. 
The error was that the drive was still busy. Could not sudo eject or unmount it either.

Next, i tried using dd to make an iso out of each disk and mounting, one at a time to /dev/cdrom. Got through the first disk ok, when the second disk was asked for, i could not umount the cdrom iso file. It behaved just like it was a real disk. 

So, question is, how can i go about installing this app, or, is there a way to override the system even as sudo  to eject the first disk when the second is requested by the installer.

thanks for any tips

---

