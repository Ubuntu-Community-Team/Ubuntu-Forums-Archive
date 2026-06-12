---
title: "NTFS Configuration Tool Inital State"
date: 2012-02-28
forum: General Help
---

### Post by Hippy Tesla on 2012-02-28
I'd like to see the first screen of the NTFS Configuration Tool when I first installed it to remove Win 7's "System Reserved" partition from auto-mounting list, but I can't seem to get to it. Is there a command in Terminal that can help me with this or is there a way to completely remove it to revert it to its initial state so I can see that screen again?

Thanks in advance!

---

### Post by raja.genupula on 2012-02-28
I can help you to make that partition as again automount with this 
[https://help.ubuntu.com/community/AutomaticallyMountPartitions#Mounting_Partitions_Automatically](https://help.ubuntu.com/community/AutomaticallyMountPartitions#Mounting_Partitions_Automatically)

look at that may be that gonna help you .

---

### Post by Hippy Tesla on 2012-02-28
I found a way! It's just to edit /etc/fstab and remove the drives you don't want to automount from the list. I know I didn't make a huge discovery, but the next time I fired up NTFS Config it recognized the partitions I deleted from fstab as new partitions and asked me if I want it to manage them. I just unticked their checkboxes and they're gone from my filesystem. Yay!

---

### Post by raja.genupula on 2012-02-29
So now you ok with your issue ? or still have something

---

