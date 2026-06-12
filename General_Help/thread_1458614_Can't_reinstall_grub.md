---
title: "Can't reinstall grub"
date: 2010-04-20
forum: General Help
---

### Post by J V on 2010-04-20
I can't reinstall grub with the current daily build disc of lucid...

```
ubuntu@ubuntu:~$ grub
The program 'grub' is currently not installed.  You can install it by typing:
sudo apt-get install grub
```

Please help, I can't boot!

---

### Post by sisco311 on 2010-04-20
It's because GRUB legacy is not installed. Since Karmic, GRUB2 is the default boot loader & manager. 

[uhelp]community/Grub2[/uhelp]

---

### Post by J V on 2010-04-20
Do I seriously have to mount the entire system just to reinstall grub? Can't I just change the MBR the same way legacy worked?

Edit: Ok done, I miss legacy :/

---

