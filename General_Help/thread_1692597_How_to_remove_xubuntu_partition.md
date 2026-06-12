---
title: "How to remove xubuntu partition ?"
date: 2011-02-21
forum: General Help
---

### Post by BADGER.BRAD on 2011-02-21
Hello all,

Can anyone tell me how to remove Xubuntu ? I installed it on a small partition on my Ubuntu machine just to see how it worked. I was very impressed but now I wish to remove it and maybe install on my older machine.

Many thanks all

Brad

---

### Post by x1a4 on 2011-02-21
Boot to windows and use its partition manager to remove the partition, then insert the windows CD, boot to it and navigate the menu to an item allowing you to fix the master boot record (to remove changes done by Xubuntu).  Boot to windows.

---

### Post by howefield on 2011-02-21
> **x1a4 said:**
> Boot to windows and use its partition manager to remove the partition, then insert the windows CD, boot to it and navigate the menu to an item allowing you to fix the master boot record (to remove changes done by Xubuntu).  Boot to windows.

How did you suss that (s)he is using windows ?

---

### Post by DanneStrat on 2011-02-21
> **BADGER.BRAD said:**
> Hello all,

Can anyone tell me how to remove Xubuntu ? I installed it on a small partition on my Ubuntu machine just to see how it worked. I was very impressed but now I wish to remove it and maybe install on my older machine.

Many thanks all

Brad

Boot into ubuntu and install "gparted" from the

repositories.

Now you may already know what partition you installed xubuntu

on. If not, try to identify it by listing your partitions

with this terminal command:

```
sudo fdisk -l
```

Now go into gparted, mark the partition containing xubuntu,

[COLOR="Red"]Be sure to select the right one,[/COLOR]

and select "delete" from the menu.

Your partition will be deleted.


Good luck.

---

### Post by BADGER.BRAD on 2011-02-22
Thanks very much  Dannestrat thats all sorted now , by the way no Windoze here for 5/6 years or so.

Brad

---

### Post by Quackers on 2011-02-22
You may need to run sudo update-grub to remove it from the grub menu.

---

