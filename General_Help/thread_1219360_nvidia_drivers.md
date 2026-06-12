---
title: "nvidia drivers"
date: 2009-07-21
forum: General Help
---

### Post by luposolo on 2009-07-21
whats the easiest way to install the latest nvidia drivers manually

---

### Post by mikewhatever on 2009-07-21
Quite frankly, there is no 'easy' way. That said, you can follow one of the numerous installation guides.

---

### Post by luposolo on 2009-07-21
well the way i did it was

1. killall gdm
2. change directory's "example cd /home/bob/Desktop
3. sh NVIDIADRIVERS
4. follow the instructions

---

### Post by Tipped OuT on 2009-07-21
The "easy" way is to go to **System< Admin< Hardware Drivers** and activate the latest drivers for your system.

---

### Post by luposolo on 2009-07-21
yeah but those nvidia drivers are out of date, ubuntu is using nvidia 180.44 and the latest is 185.18.14

---

### Post by Tipped OuT on 2009-07-21
> **luposolo said:**
> yeah but those nvidia drivers are out of date, ubuntu is using nvidia 180.44 and the latest is 185.18.14

Then download and install them from nVidia's website. Ask for help if you don't know how to install it. This is why we're here. :)

---

### Post by luposolo on 2009-07-21
ok i installed the latest nvidia drivers but when i try to launch WoW it gives me "failed to find suitable display device", compiz is running fine but i dont why WoW wouldnt work

---

### Post by devildoc5 on 2009-07-21
it is possible that your "version" of ubuntu kernel is not compatible with the new nvidia driver......That would make sense too, seeing as how ubuntu does not recommend it yet....

---

### Post by 3rdalbum on 2009-07-21
> **luposolo said:**
> yeah but those nvidia drivers are out of date, ubuntu is using nvidia 180.44 and the latest is 185.18.14

So? It works, doesn't it?

@Devildoc5: No, the latest Nvidia drivers are compatible with the current Ubuntu kernel.

---

### Post by Chemical Imbalance on 2009-07-21
Once you install the nvidia drivers from the unix page manually, all you have to do to upgrade to a later version is 
```
sudo nvidia-installer --update
```

[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

---

