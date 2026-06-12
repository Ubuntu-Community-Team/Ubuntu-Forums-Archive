---
title: "dd for cloning an image to a partition"
date: 2011-04-13
forum: General Help
---

### Post by avatarmonkeykirby on 2011-04-13
Hello, I have a binary image that I can copy to a partition and have done so successfully in the past. The image is smaller than the partition size, and everything is all good. However, I noticed that in copying the 5 gb image to the 9 gb partition there are 4 gb that are unnoticed by the system. It still registers the partition at the correct size in Gparted and Disk Utility. How can this be remedied so the whole filesystem is copied and doesn't lose the extra space? Thanks

---

### Post by Quackers on 2011-04-13
Have a look at the first couple of posts in this thread

[http://ubuntuforums.org/showthread.php?t=1242394&highlight=resize2fs](http://ubuntuforums.org/showthread.php?t=1242394&highlight=resize2fs)

---

### Post by avatarmonkeykirby on 2011-04-13
Thanks for that, it worked like a charm!

And for the benefit of others, this does work on the CR48. While in Chrome, enter in the terminal and use
```

resize2fs -p /dev/sda7

```

I've got my full partition now. Bamf!

---

### Post by Quackers on 2011-04-13
Niiiiiiiiiice :-)  Thanks to Herman!
Please mark the thread as solved using the Thread Tools near the top of the page.

---

