---
title: "Mount windows network drive"
date: 2006-03-03
forum: General Help
---

### Post by FaZZy on 2006-03-03
how do i mount a windows hardrive over det network......i dont want it on my desktop becuse when i mount it ther dcpp cant list it.... plz help

---

### Post by Cephyr on 2006-03-03
Well, first of all, make sure that the drive on the Windows computer is marked as "Shared".

Allright, now on your Linux machine make sure you've installed the packeage "smb". This is the service that Windows uses to share files.

Now, if you don't have it on your desktop already, right click the desktop and create a launcher. Name it "network servers" and type "nautilus network:" in the command box. Click "ok" and you should be ready to rock and roll!

---

### Post by FaZZy on 2006-03-04
i want to have a virutal drive like you have in windows under "my computer". if i mount the drive on desktop dcpp cant find it...i want this drive to be my download folder.

---

