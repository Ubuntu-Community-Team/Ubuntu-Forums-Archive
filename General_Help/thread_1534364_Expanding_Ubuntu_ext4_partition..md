---
title: "Expanding Ubuntu ext4 partition."
date: 2010-07-19
forum: General Help
---

### Post by welshmike on 2010-07-19
Below is my hard drive partitioning.

I would like to extend /dev/sda5 to include the space currently occupied by /dev/sda3 . I'd previously deleted sda3 and tried using GParted but it would not use the empty space, even when run off a live CD image.
Does the team have any ideas how I could use the unwanted space currently occupied by sda3 and include it as part of sda5?

[IMG]http://www.cccc.hostoi.com/GParted.png[/IMG]

---

### Post by kaelspencer on 2010-07-19
I've run into this issue before as well. When using GParted from a live CD, typically your swap partition will be locked (the little keys). Right click, tell it to not use the swap partition. Then you should be able to resize your extended partition, and then resize sda5 to use the free space.

---

### Post by welshmike on 2010-07-19
kaelspencer,

Thank you very much. That was very helpful information.
I've now recovered the space that was used by Windows XP and am using it for my preferred Ubuntu system as below:
[IMG]http://www.cccc.hostoi.com/Screenshot.png[/IMG]
So having moved from XP to dual boot Ubuntu and XP I'll soon be looking to remove XP and only run it only when absolutely necessary as a Guest of Ubuntu under VirtuaBox.

---

