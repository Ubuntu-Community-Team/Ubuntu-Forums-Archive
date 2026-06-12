---
title: "can you format 2gb memory card as 1gb"
date: 2011-03-27
forum: General Help
---

### Post by rebeltaz on 2011-03-27
I know this is going to sound stupid, but I have a few 2gb CompactFlash memory cards that I bought to use with my FujiS7000 digital camera. Only problem is that that camera will only read/write to 1gb memory cards. I don't suppose there's any way to format these 2gb cards so that the camera sees them as 1gb cards?

---

### Post by DeMus on 2011-03-27
Is it possible to make a 1GB partition on it and format that one? Or in the best case scenario, make 2 1GB partitions and use both. I have no idea if this works, I'm just guessing here.

---

### Post by rebeltaz on 2011-03-27
> **DeMus said:**
> Is it possible to make a 1GB partition on it and format that one? Or in the best case scenario, make 2 1GB partitions and use both. I have no idea if this works, I'm just guessing here.

Not sure.. how would I go about doing that?

---

### Post by DeMus on 2011-03-27
> **rebeltaz said:**
> Not sure.. how would I go about doing that?

Install gparted (it's in the repos so you can use Synaptic). In gparted choose the disk. BE CAREFUL you choose the right disk and create a partition on it. I guess there is no need to format it, the camera will do that probably for you. If not, format it as FAT32 which should be recognized by the camera.
Success.

---

### Post by rebeltaz on 2011-03-27
d'oh! gparted! I use that all the time as a standalone bootable cd when I am working on computers but I didn't think about installing it on my system to use within the OS. I'm so used to using fdisk and mkdosfs from the command line that gparted didn't even hit me.

Anyway, I tried that and no go. The camera still doesn't want to see it...   :(

---

### Post by DeMus on 2011-03-27
> **rebeltaz said:**
> d'oh! gparted! I use that all the time as a standalone bootable cd when I am working on computers but I didn't think about installing it on my system to use within the OS. I'm so used to using fdisk and mkdosfs from the command line that gparted didn't even hit me.

Anyway, I tried that and no go. The camera still doesn't want to see it...   :(

Well, it was a try. I also was not sure it would work, but if you don't try you'll never know.
Sorry, but then I can't help you anymore, maybe somebody else knows a way. Success.

---

### Post by rebeltaz on 2011-03-27
no problem... you're right - it never hurts to try. thanks anyway.

---

