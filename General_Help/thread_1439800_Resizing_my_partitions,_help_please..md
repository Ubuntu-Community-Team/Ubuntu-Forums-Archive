---
title: "Resizing my partitions, help please."
date: 2010-03-26
forum: General Help
---

### Post by Djdubx2 on 2010-03-26
Ok, So I won't to resize the partition on my laptop that I have Ubuntu on. I put 20 GB for the partition, but I'm not even using 10 GB. What I want to do is shrink it down to 10 GB and give the reset back to my Windows7 partition. 

So would it be ok to just go into gparted and resize it? Also when I restart my laptop and try to go into windows7 will it automaticaly fix and resize its partition with the 10 GB I take out of Ubuntu?

---

### Post by derande on 2010-03-26
yes it will work if you use the Gparted live CD but make sure to always backup before futzing with partitions.

[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

---

### Post by Djdubx2 on 2010-03-26
OK thanks. 

I'll make sure to back up my stuff before doing anything with the partitions.

---

### Post by 2hot6ft2 on 2010-03-26
A screenshot of the drive in GParted would help since if your linux swap and the partition you wish to change are both inside an extended partition you will need to right click the swap partition and select swap off to unlock the swap partition and you would also have to select the extended partition and right click and un-mount.

The livecd will automatically mount an available swap partition.
> **Djdubx2 said:**
> Also when I restart my laptop and try to go into windows7 will it automaticaly fix and resize its partition with the 10 GB I take out of Ubuntu?
No, you would have to do it with the Drive Management tool in windows. It wont just magically do it for you without you telling it to. And actually once you tell it to it will do it when you reboot since it can't do it while you're in windows.

---

