---
title: "Giving permission to hard drive"
date: 2010-01-24
forum: General Help
---

### Post by Skater91411 on 2010-01-24
Alright I've got 2 hard drives in my computer and one of them has no data on it so I have to mount it to open it and once I do this it asks for a password to mount it. If I could get this problem fixed it would be great but not a complete necessity.

---

### Post by pastalavista on 2010-01-24
You can edit /etc/fstab but simpler (for me to explain) is to download Storage Device Manager and do it with a GUI ```
sudo apt-get install pysdm
```
It will appear in the System--> Administration menu

---

### Post by bodhi.zazen on 2010-01-25
Moved to general help.

It depends on the file system, FAT/NTFS are different from ext2/3/4

See: [How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by SuperSonic4 on 2010-01-25
If you want to mount it on boot then specify it in fstab as per bodhi.zazen's link above.

If you want to mount it occasionally you may want to consider giving your user mount permissions in /etc/sudoers

---

### Post by bodhi.zazen on 2010-01-25
> **SuperSonic4 said:**
> If you want to mount it on boot then specify it in fstab as per bodhi.zazen's link above.

If you want to mount it occasionally you may want to consider giving your user mount permissions in /etc/sudoers

You can use the options noauto in combination with user or users in /etc/fstab and then a user or users will be able to mount w/o modifying sudo (/etc/sudoers).

To edit /etc/sudoers please use visudo (sudo visudo). visudo checks syntax for errors.

---

### Post by SuperSonic4 on 2010-01-25
> **bodhi.zazen said:**
> You can use the options noauto in combination with user or users in /etc/fstab and then a user or users will be able to mount w/o modifying sudo (/etc/sudoers).

To edit /etc/sudoers please use visudo (sudo visudo). visudo checks syntax for errors.

Even better :) although wouldn't it still mount at boot?

---

### Post by bodhi.zazen on 2010-01-25
> **SuperSonic4 said:**
> Even better :) although wouldn't it still mount at boot?

in the options column, use the option noauto (to keep the HD from mounting automatically) if you wish.

---

### Post by Skater91411 on 2010-01-25
Uhh ya, thats a little more complicated than I was looking forward to as im a pretty new Linux user and dont get me wrong I always look for a learning experience but it not too big of a deal. So thanks anyway to whoever replied.:D

---

### Post by pastalavista on 2010-01-25
> **Skater91411 said:**
> Uhh ya, thats a little more complicated than I was looking forward to as im a pretty new Linux user and dont get me wrong I always look for a learning experience but it not too big of a deal. So thanks anyway to whoever replied.:D

Storage Device Manager is also in the Software Center. Install it.. easy.

---

