---
title: "USB drives and partitions read only."
date: 2011-11-04
forum: General Help
---

### Post by raj3003 on 2011-11-04
Hello...

I'm using Ubuntu from past 2 weeks...

I'm facing the same issue not only with USB HDD. I have 4 partitions of my HDD, out of which one is used for Windows 7, the another 1 is for Ubuntu, rest 2 partitions are used for storing data.

It was fine since I ran an update in the evening, after the update was successful. Both the partitions of my hard drive and USB HDD are mounted as Read only.

When I tried to change the permissions through nautilus, I am getting an error stating "Failed to run nautilus as user root".

Can anyone help me to resolve this issue.

---

### Post by coffeecat on 2011-11-04
@raj3003, I've moved your post onto its own thread with what I hope is a suitable title. Please do not jump onto other threads.

---

### Post by Anayonkar.Shivalkar on 2011-11-04
@raj3003,

Try installing ntfs-3g. It will warn you about removal of ntfsprogs. Say yes and proceed. Once ntfsprogs is gone and ntfs-3g is installed, remount partitions and try. You might also need to reboot machine.

Hope this helps.

---

