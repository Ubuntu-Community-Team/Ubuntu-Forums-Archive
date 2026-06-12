---
title: "Login screen problem"
date: 2011-09-11
forum: General Help
---

### Post by viswanathk on 2011-09-11
Hello UF,

Recently I got tired with Gnome3 and installed recent version of KDE in my computer. But as you know, KDE is slower than Gnome3 and I plan to switch to Gnome3 when it comes out of the beta stage. So I did not remove it. My problem now is that, the login screen is pathetic. I tried changing it from KDE, but whatever theme I install it will not change the login screen. The login screen is the same old Gnome3 login screen. Also there is another problem. Whenever I logout of KDE I get brief glimpse of my Gnome3 desktop. I mean the wallpaper, the icons etc. How can I remedy it? Any ideas?:confused:

---

### Post by Krytarik on 2011-09-11
How about just trying KDM then, the display manager meant for KDE!?:
```
sudo apt-get install kdm
```Hopefully, this also fixes your other issue.

If you want to change it again later, just run one the following commands, depending on which display manager you have installed at that time. Each of those will present you with a screen to eventually choose the desired display manager:
```
sudo dpkg-reconfigure gdm
sudo dpkg-reconfigure lightdm
sudo dpkg-reconfigure kdm
```Greetings.

---

### Post by viswanathk on 2011-09-11
> **Krytarik said:**
> How about just trying KDM then, the display manager meant for KDE!?:
```
sudo apt-get install kdm
```Hopefully, this also fixes your other issue.

If you want to change it again later, just run one the following commands, depending on which display manager you have installed at that time. Each of those will present you with a screen to eventually choose the desired display manager:
```
sudo dpkg-reconfigure gdm
sudo dpkg-reconfigure lightdm
sudo dpkg-reconfigure kdm
```Greetings.

Ah thank you. Solved ;)

---

