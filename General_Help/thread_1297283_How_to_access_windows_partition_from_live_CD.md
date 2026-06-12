---
title: "How to access windows partition from live CD"
date: 2009-10-21
forum: General Help
---

### Post by chumchum on 2009-10-21
Hello

My Windows is screwed and just won't boot anymore, I was recommended to perform a system recovery. Since XP doesn't start I can't back up the data from there so I thought I'd do it by burning DVDs in Ubuntu, loaded from a live CD (I've Gutsy 7.10).

Is there anyway for me to mount my windows partition (without installing Linux) and make copies?

Thanks in advance

---

### Post by mikewhatever on 2009-10-21
If the file system is not damaged, you could mount the partition from the file browser simply by clicking on it. All partition should be listed in the left panel.

---

### Post by fluffman86 on 2009-10-21
Not sure if this worked in Gutsy Gibbon, but you should just be able to go to Places and click on your Windows partition. 

If that doesn't work, then go to Applications > Accessories > Terminal and type:
```
sudo mkdir /media/win
sudo mount /dev/sda1 /media/win -t ntfs-3g -o force
```
Where sda1 is the first partition of your hard drive.  This is usually right, unless you have a recovery partition (like from compaq or HP).  Then you would use sda2.

If the command works, but mounts your recovery partition, then you can try again with:
```
sudo mkdir /media/win2
sudo mount /dev/sda2 /media/win2 -t ntfs-3g -o force
```

Hope that works.

Edit: Once you do that, the drive should either show up under the Places menu at the top of your screen, or it should output an error for you to post here.

---

### Post by chumchum on 2009-10-21
Ah perfect, that worked great, thanks!

---

