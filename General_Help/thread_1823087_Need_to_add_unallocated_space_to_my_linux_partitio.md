---
title: "Need to add unallocated space to my linux partition"
date: 2011-08-11
forum: General Help
---

### Post by ravij96 on 2011-08-11
Hi I'm trying to add unallocated space to my linux partition but need help doing so. I am also willing to delete my linux partition and starting from the start since I don't have any important files on linux. I tried deleting the extended partition, which would make about 80gb of unallocated space, then installing Linux to that but it didn't work. I tried doing this from the LiveCD. I'll add a picture of my Gparted. The unallocated space is 50 gb.

---

### Post by sanderd17 on 2011-08-11
Where do you want that 50GB to go to?

You might need to expand sda3 before you can expand the partition you want (sda6).

Also, you can delete the second swap partition. Having two swap partitions is useless.

---

### Post by ravij96 on 2011-08-11
I want to add it to sda6

---

### Post by sanderd17 on 2011-08-11
Ok, than you right click on sda3, resize it and expand it to take the entire 50GB, right click on sda6, and do the same.

---

### Post by ravij96 on 2011-08-11
When I try to do this gparted says that my computer may be unbootable after this because it can mess grub up. That's why I'm asking here because I already tried what you said and I got that popup.

---

### Post by sanderd17 on 2011-08-11
Hmm, normally it will give no problems, but to be sure, run

```

sudo update-grub

```

after resizing it, it will reset all references of GRUB to the right partitions.

---

### Post by ravij96 on 2011-08-11
Alright I'll post back after doing so.

---

### Post by sanderd17 on 2011-08-11
And for the case you can't boot again, you will have to repair the mbr with this method: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

As long as you have a Live CD, nothing is lost

---

### Post by ravij96 on 2011-08-11
Hey thanks for your help I didn't run into any problems and now have another 50gb added into my linux partition.

---

