---
title: "how to change grub to boot xp first?"
date: 2010-03-17
forum: General Help
---

### Post by dansar99 on 2010-03-17
How could I change the grub to boot into windows xp first instead of ubuntu on my dual boot machine? Dan

---

### Post by JC Cheloven on 2010-03-17
First start the pc and see which position your xp has in the grub menu, from the top. Starts counting from zero, and every input counts.

Second, edit the proper file, ie:
```
gksudo gedit /etc/default/grub 
```

You'll see a line like ```
GRUB_DEFAULT=0
```
Simply change "0" for the position occupied by the xp entry.

In a terminal run ```
sudo update-grub
```

Then reboot.

---

### Post by Swagman on 2010-03-17
or install startup-manager and select XP as your default.

---

### Post by dansar99 on 2010-03-17
> **JC Cheloven said:**
> First start the pc and see which position your xp has in the grub menu, from the top. Starts counting from zero, and every input counts.

Second, edit the proper file, ie:
```
gksudo gedit /etc/default/grub 
```

You'll see a line like ```
GRUB_DEFAULT=0
```
Simply change "0" for the position occupied by the xp entry.

In a terminal run ```
sudo update-grub
```

Then reboot.

Thank you!!!  Much appreciated. Dan

---

### Post by Penguin Guy on 2010-03-17
> **dansar99 said:**
> Thank you!!!  Much appreciated. Dan
It helps other people find what they are looking for if you mark you threads as solved once you have found your answer. You can do this by clicking [COLOR="Green"]Thread Tools -> Mark as Solved[/COLOR]. Thanks.

---

