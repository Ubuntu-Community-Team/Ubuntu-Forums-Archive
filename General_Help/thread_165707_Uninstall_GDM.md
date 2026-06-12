---
title: "Uninstall GDM"
date: 2006-04-25
forum: General Help
---

### Post by Don_Toni on 2006-04-25
Hi, I make mistake - I'm uninstallt GDM, restart and now I can't boot my Ubuntu. Please help me. On the screen I see:> Ubuntu 5.10 "Breezy Badger" ubuntu tty2
ubuntu login
I'm login in my account but i can boot the Ubuntu.

---

### Post by aysiu on 2006-04-25
You can't log in, or you can't log in *graphically*?

If you can log in in text-mode, just type this ```
sudo apt-get update
sudo apt-get install gdm
sudo /etc/init.d/gdm restart
```

---

### Post by Don_Toni on 2006-04-25
[QUOTE=aysiu]You can't log in, or you can't log in *graphically*?

If you can log in in text-mode, just type this ```
sudo apt-get update
sudo apt-get install gdm
sudo /etc/init.d/gdm restart
```[/QUOTE]
Thanks a lot, Aysiu. You are very helpfull.:)

---

### Post by malQi on 2006-04-25
you dont need gdm to start gnome/kde/xfce or other graphical env. in text mode just type "startx"

---

