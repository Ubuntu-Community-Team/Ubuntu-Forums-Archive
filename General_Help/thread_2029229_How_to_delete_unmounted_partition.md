---
title: "How to delete unmounted partition?"
date: 2012-07-19
forum: General Help
---

### Post by Nablet on 2012-07-19
Hello

I had ntfs partition on my hard disk drive, but I had decided to resize my sda1 so I had to use gparted and unmount and remove that partition.
Now everytime my ubuntu starts [10.04 lts] it says "blablabla can't mount /ntfsfpartition blablabla] and I have to skip mounting everytime [its a bit confusing]. Sorry for my language - I am newbie/noob/nablet.

My /ntfspartition was mounted in sda5 and now my swap is mounted in sda5 [is it a problem?].

How to delete that /ntfspartition to be free of that skipping?

---

### Post by Wirephire on 2012-07-19
/etc/fstab is the file that contains information of all the partitions that exist on your Ubuntu system.
You need to have root permision to change this file so use:
```
sudo *yourfavouriteditor* /etc/fstab
```to edit it. Just find the line that contains the partition you removed and delete it.
If you don't understand this file or you're not sure which line to remove, tell us what the command
```
sudo fdisk -l
```gives you and we'll help you.


~wph

---

### Post by Nablet on 2012-07-19
Thank you, it worked!

---

