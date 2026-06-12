---
title: "File check?"
date: 2009-06-25
forum: General Help
---

### Post by KegHead on 2009-06-25
Hi!

It seems like about every 20-25-30 times I boot up, Ubuntu does a file/system check.

Is there any way to perform this at will or at a specified time?

Thanks!

KegHead

---

### Post by XCan on 2009-06-25
This entry in the forums may help you: [http://ubuntuforums.org/showthread.php?t=300477](http://ubuntuforums.org/showthread.php?t=300477) .

---

### Post by michy99 on 2009-06-25
By default it checks every 30 boots. You can change it with tune2fs. To see how to use it, read the  man page.```
man tune2fs
```

---

### Post by Cheesemill on 2009-06-25
Or you can force it to happen on next boot by doing:
```
sudo touch /forcefsck
```

---

