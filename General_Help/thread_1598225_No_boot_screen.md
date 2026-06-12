---
title: "No boot screen"
date: 2010-10-16
forum: General Help
---

### Post by kanishkdudeja on 2010-10-16
ive recently installed ubuntu 10.10.. but it does show any boot screen..even in ubuntu 10.04 it showed no boot screen..it just displays a black screen for 5-6 second..why is this happening ?

---

### Post by Quackers on 2010-10-16
If you only have one operating system installed grub deosn't show the menu by default. If you hold down the shift key during boot the grub menu will show. You can adit /etc/default/grub and change its behaviour.

---

### Post by kanishkdudeja on 2010-10-16
ok il check it out and tell you if it works out..:)..thanks anyway

---

### Post by l0co on 2010-10-22
It's not a point, I think. Do you mean plymouth animation? I don't see any in my yesterday ubuntu installation. It can be problem with proprietary video driver: [http://ubuntuforums.org/showthread.php?t=1597231](http://ubuntuforums.org/showthread.php?t=1597231)

---

