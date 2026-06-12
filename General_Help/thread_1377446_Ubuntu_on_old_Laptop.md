---
title: "Ubuntu on old Laptop"
date: 2010-01-10
forum: General Help
---

### Post by fbjoey on 2010-01-10
I have Ubuntu on my laptop but it can be a bit slow at times. Do you think it would be a good idea to put Kubuntu or Xubuntu onto it instead. Whats the real difference between them and can I use the same applications on them?

---

### Post by NoaHall on 2010-01-10
The only difference between them is what Desktop Environment they use(DE). Ubuntu uses Gnome, Kubuntu use KDE, Xubuntu uses XFCE. To be quicker, XFCE is the ideal one out of those. To install it, simply run
```
sudo apt-get install xubuntu-desktop --no-install-recommends
```
You can use the same applications on every DE and WM.

---

### Post by fbjoey on 2010-01-10
Awesome. I will give it a go. Is it easy to change back if I don't like it?

---

### Post by NoaHall on 2010-01-10
> **fbjoey said:**
> Awesome. I will give it a go. Is it easy to change back if I don't like it?

Yep, you will even keep Gnome(your current DE) installed. All you need to do to change which one is used, is to click the "options" on the login screen, and change "session" to "XFCE"

---

### Post by atomizer on 2010-01-10
I would also disable services you don't need (like bluetooth)
you will gain a few MB of your memory. (offcourse only if you don't need the services)

Xubuntu desktop is the way to go, an even better dektop is OpenBox, but you need to configure a bit to get a easy to use desktop.(but it is VERY lightweight)

---

