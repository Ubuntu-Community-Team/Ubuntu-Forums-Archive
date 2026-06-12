---
title: "Unable to Launch Files Unless Navigating Using Nautilus First"
date: 2012-09-18
forum: General Help
---

### Post by SteelReserve on 2012-09-18
I have a shortcut on my desktop for a playlist of MP3 files that reside on a secondary hard drive.  If I try launching the shortcut after booting, the files are not found.  If I simply navigate to the root of the secondary drive using Nautilus and then go back and launch the shortcut, everything works fine.  How can cut out this extra step?  Thanks.

---

### Post by newb85 on 2012-09-18
The issue is that the secondary HD is not mounted yet.  You can set it up to mount at startup, and that would eliminate the extra step.

Please read how:
[https://help.ubuntu.com/community/AutomaticallyMountPartitions]("https://help.ubuntu.com/community/AutomaticallyMountPartitions")

---

### Post by SteelReserve on 2012-09-19
> **newb85 said:**
> The issue is that the secondary HD is not mounted yet.  You can set it up to mount at startup, and that would eliminate the extra step.

Please read how:
[https://help.ubuntu.com/community/AutomaticallyMountPartitions]("https://help.ubuntu.com/community/AutomaticallyMountPartitions")

The drive is already mounted during boot, but I'm still getting the error "Location Not Found".  The drive is always visible in Nautilus.  Once I click into the drive, I can open any shortcuts pointing to files on it.

---

### Post by newb85 on 2012-09-19
> **SteelReserve said:**
> The drive is already mounted during boot, but I'm still getting the error "Location Not Found".  The drive is always visible in Nautilus.  Once I click into the drive, I can open any shortcuts pointing to files on it.

Don't misunderstand. I'm not trying to argue.  I'm trying to understand.  Why do you think the drive is mounted during boot?

FYI, available drives that are not yet mounted are still visible in Nautilus.  When you click on them, Nautilus mounts them.

---

### Post by SteelReserve on 2012-10-06
You were correct, thank you.  The drive wasn't being mounted upon booting.  Everything is working great now!!!

---

### Post by newb85 on 2012-10-06
Glad to hear it.  Please mark the thread as solved by clicking on the Thread Tools link at the top.

---

