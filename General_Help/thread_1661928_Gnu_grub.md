---
title: "Gnu grub"
date: 2011-01-07
forum: General Help
---

### Post by zainlodhi on 2011-01-07
Before booting my GNU GRUB shows different option such as Linux-generic, Linux (recovery mode), Memory test and one more option. What are these different options and how to remove these if they are not required.
Regards

---

### Post by Quackers on 2011-01-07
Every time a new kernel is installed (via updates) 2 new entries will appear in the grub menu (Linux-Generic and Linux recovery mode). So you can end up with quite a few entries. It is recommended that the current kernel plus one previous kernel be kept, for emergency reasons.
It is also recommended that the recovery mode be kept in case the Linux Generic kernel fails (sometimes caused by a update).
However I, for one, tend to keep only the current kernel and the last kernel, deleting the recovery mode entries from the menu.
To delete the recovery mode entry open up a terminal and run ```
sudo sed s/'#GRUB_DISABLE_LINUX_RECOVERY="true"'/'GRUB_DISABLE_LINUX_RECOVERY="true"'/g -i /etc/default/grub
```
The Memtest entry is a memory test program. This entry can be removed, if required, by another terminal entry ```
sudo chmod -x /etc/grub.d/20_memtest86+
```

---

