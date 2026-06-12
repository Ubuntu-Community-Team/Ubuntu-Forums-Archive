---
title: "grub not showing window"
date: 2009-08-30
forum: General Help
---

### Post by chunwwe on 2009-08-30
I have window xp on both partition c and partition d. And today i formatted my c drive and reinstall a fresh windows xp on it. so when i turn on my computer today the grub screen doesnt show up and it boots from drive c. So how do i get grub to show up again so that i can boot from drive d and ubuntu?

---

### Post by Vishnu V on 2009-08-30
Boot from the ubuntu live cd and open the terminal and type

```
sudo grub
```

```

grub> find /boot/grub/stage1

```
it will return something like 
find /boot/grub/stage1
(hdX,Y)
then copy the returned value in the end of root as shown blew
```

grub> root (hdX,Y)
grub> setup (hd0)
grub> quit

```
then reboot your computer

---

