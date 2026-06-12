---
title: "problem with Ubtuntu/fedora"
date: 2010-06-29
forum: General Help
---

### Post by Odaym on 2010-06-29
I had Lucid installed, and i inserted a cd for Fedora, i chose the option to "Shrink to make size of new OS",
it kept on "Resizing sda1" until everything was installed and etc.. now i start and i cant see any multi boot option, and i load directly into fedora, but i can see my files on Ubuntu through a mounted disk whose size has the size that i chose for "Shrink disk to : ...."
how do i get my ubuntu back and make it run alongside fedora?
thank you very much in advance

---

### Post by abdulapopoola on 2010-06-29
You have to look for a way that GRUB will be able to load your Lucid, I'm a newbie and don't know much about that yet but you should search online. 
Most probably the grub.conf file should solve it but you have to be very careful.

---

### Post by garvinrick4 on 2010-06-29
> **Odaym said:**
> I had Lucid installed, and i inserted a cd for Fedora, i chose the option to "Shrink to make size of new OS",
it kept on "Resizing sda1" until everything was installed and etc.. now i start and i cant see any multi boot option, and i load directly into fedora, but i can see my files on Ubuntu through a mounted disk whose size has the size that i chose for "Shrink disk to : ...."
how do i get my ubuntu back and make it run alongside fedora?
thank you very much in advance Put in a LIve CD and reinstall grub2, right now
grub legacy which is fedoras grub of choice is running. When you say shrink to fit size you mean it shrunk the Ubuntu partition to make room for fedora. Never have used that but do run fedora so I could see how yum is verses apt-get. If you do not know how to reinstall grub2 just ask here on this thread.

---

### Post by QIII on 2010-06-29
I like Fedora 13, but man!  GRUB?  They are behind the times.

(I run Fedora in a virtual machine, by the way.  No shutting down, going through GRUB2, shutting down again to get back to Ubuntu, etc.)

---

### Post by Odaym on 2010-06-29
I don't know how, i put in the ubuntu live cd first? i have that

---

### Post by Odaym on 2010-06-29
I used this, [grub2 installation]("http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html"), and it worked..but now i can't see fedora :o lol-enducing indeed!

---

### Post by garvinrick4 on 2010-06-29
Update grub so grub2 can see other installs

```
sudo update-grub
```
```
sudo grub-mkconfig
```

---

