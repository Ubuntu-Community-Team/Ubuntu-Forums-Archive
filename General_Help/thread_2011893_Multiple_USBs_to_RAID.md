---
title: "Multiple USBs to RAID"
date: 2012-06-28
forum: General Help
---

### Post by jacobroecker on 2012-06-28
Alright people.  Random question.  Is it possible to set up several USB drives as a raid?  I've got a few drives lying around that by themselves are small, but combined could be quite useful.

If it's possible, then someone running linux has likely figured it out, I just need to know how, or who.

Thanks in advance!

-Jacob

---

### Post by hunter.allen on 2012-07-02
It is certainly a possibility (for the most part).

RAID requires a RAID controller, which I don't see as a possibility for USB's.  

However, if you want to write files across USB drives in a RAID-like system, you can use a Logical Volume Manager (LVM) to do so (this I have done before with several drives on my server). This you can read about [here]("http://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux)"). 

For a tutorial with Ubuntu setup, go to this [link]("http://www.howtogeek.com/howto/40702/how-to-manage-and-use-lvm-logical-volume-management-in-ubuntu/"). 

Enjoy playing with your USB drives!
-Hunter A.

---

