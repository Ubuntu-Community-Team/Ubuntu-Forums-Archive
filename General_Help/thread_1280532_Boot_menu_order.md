---
title: "Boot menu order"
date: 2009-10-02
forum: General Help
---

### Post by tuahaa on 2009-10-02
You know how if you have two or more operating systems? Well, the thing is my mum uses windows a lot and she doesn't ever accept Linux. Anyway, she usually turns on the computer while she does something else. However, it automatically goes in to Ubuntu after 10 seconds. The only way to get XP is to use the arrow keys which wastes her time, etc.

Is it possible to put XP on top of the list so it is highlighted first? 

Thanks guys

---

### Post by pmlxuser on 2009-10-02
well do 
```

$ sudo nano /grub/boot/menu.lst

```

you will see the word default on an ubuntu entry...
move the default word to be on windows entry....

viola 
ps: backing the menu.lst file is good practise. in case things don't work out...

---

### Post by wojox on 2009-10-02
And when your done editing update grub:

```
sudo update-grub
```

---

### Post by Giblet5 on 2009-10-02
I use "default=saved" and turn on the "savedefault" option for every entry except memtest and recovery modes. That way, it will reboot to whatever I was using last...

---

### Post by pmlxuser on 2009-10-02
> **Giblet5 said:**
> I use "default=saved" and turn on the "savedefault" option for every entry except memtest and recovery modes. That way, it will reboot to whatever I was using last...

Good one, 1 problem though if he/she is the last one to use the computer with ubuntu. Mom will be P***sed because its going to boot ubuntu.. 

the option of putting windows in menu.lst default is good because mother will always be happy

---

### Post by tuahaa on 2009-10-05
Thanks guys! Forgot to check this thread. Helped me out a lot...

---

