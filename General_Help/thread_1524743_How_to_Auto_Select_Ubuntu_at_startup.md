---
title: "How to Auto Select Ubuntu at startup"
date: 2010-07-05
forum: General Help
---

### Post by idrivefast on 2010-07-05
Aloha,
I know this must be out there somewhere but I can't find the answer. When I boot my computer there is a screen the lists all versions of Ubuntu and also a Windows partition. How can I have it auto select the latest version of Ubuntu?

Mahalo

---

### Post by mike555 on 2010-07-05
in package manager , get "startup manager" ... it will let you set the one you want....

---

### Post by kiddykoff on 2010-07-05
are you using grub legacy or grub 2?

If you are using legacy, It should be just as simple as moving your desired entry to the top of the list.

run
```
gksudo /boot/grub/menu.lst
```

I can't elaborate more, because i'm using grub2 and i don't remember much more.

If you're using grub2 than this thread can be useful. [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

