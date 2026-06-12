---
title: "Two Hard Drives"
date: 2010-04-15
forum: General Help
---

### Post by waltwin on 2010-04-15
[SIZE=2]I have two hard drives. On one I have ubuntu 9.04 and on the second I have Windows XP PRO. I would like to switch between between drives without going through the bios routine. I am told I need a Dual Boot Script but I have not found one. Does anyone have an idea.

Thank you for looking at my problem.

waltwin[/SIZE]

---

### Post by Don1500 on 2010-04-15
Install Ubuntu AFTER you install windows and you should have GRUB on the MBR. This will give you a startup screen to select which OS you want to use.

If you have both windows and Ubuntu installed already, load into Ubuntu and in the terminal type ```
sudo apt-get install grub
``` this should do it.

If you still have problems, reinstall Ubuntu. that should take care of everything.

---

### Post by WinterRain on 2010-04-15
> **Don1500 said:**
> Install Ubuntu AFTER you install windows and you should have GRUB on the MBR.

He obviously unplugged one drive while installing on the other, hence having to use the BIOS to choose which drive to use. I suggest going [here]("https://help.ubuntu.com/community/Grub2") and reinstalling grub while both drives are connected.
> **Don1500 said:**
> 
If you still have problems, reinstall Ubuntu. that should take care of everything.
With all due respect, that's overkill, as there are easier solutions.

---

### Post by waltwin on 2010-04-15
I tried your suggestion but no joy. Thank you for your input.

waltwin

---

### Post by 3rdalbum on 2010-04-15
With both hard disks plugged in, try:

```
sudo update-grub
```

in the terminal in Ubuntu.

---

### Post by waltwin on 2010-04-16
Tried your suggestion but, no joy. I guess I will have to go the bios route. Thank you for your input. Sure seems like there should be a way to accomplish this though! I guess that's why programers make the big bucks. Thank you for your input.

waltwin

---

