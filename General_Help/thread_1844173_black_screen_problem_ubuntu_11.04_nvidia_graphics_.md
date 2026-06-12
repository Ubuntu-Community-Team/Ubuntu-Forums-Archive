---
title: "black screen problem ubuntu 11.04 nvidia graphics card"
date: 2011-09-14
forum: General Help
---

### Post by MilesEpps on 2011-09-14
i don't know if this is in the wrong category but, when i install the additional driver for my graphics card my screen goes black (it is the correct driver), this driver (nvidia 173) used to work but now as soon as i log in i get black screen, plus i cant use grub. unfortunately this made me reinstall ubuntu. please help!!! Plus if anyone knows if the palit Geforce GT 440 or Sapphire  11168-02-20R HD 5670 (think thats what its called) are any good as i am thinking of upgrading.

thanks

---

### Post by TeoBigusGeekus on 2011-09-14
AFAIK, better go for the nvidia one.
As for the driver, if it does this to you again, boot into recovery mode and delete your xorg.conf
```
sudo rm /etc/X11/xorg.conf
```
Then
```
sudo reboot
```
Why don't you use the 173 driver, if it works for you?

---

### Post by MilesEpps on 2011-09-15
last time i tried it wouldn't let me scroll down the grub boot menu or choose anything.

---

### Post by MilesEpps on 2011-09-15
thanks for the help but my computer booted normally (although, I'll probably need it in the future because every computer i touch breaks :D ).

---

