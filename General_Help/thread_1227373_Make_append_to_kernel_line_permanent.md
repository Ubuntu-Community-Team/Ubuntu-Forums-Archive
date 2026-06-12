---
title: "Make append to kernel line permanent"
date: 2009-07-30
forum: General Help
---

### Post by user 123 on 2009-07-30
I've had to append the kernel line in grub to solve a problem I was having. However this only works once and I have to append the line everytime I boot. Is there any way to make the append permanent?

---

### Post by wojox on 2009-07-30
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by sisco311 on 2009-07-30
Yep, wojox is right, you have to edit the menu.lst file.

Add your option to the:
```
#kopt=....
```
line and run the:
```
sudo update-grub
```command.

For more info please read this guide: [https://help.ubuntu.com/community/GrubHowto#Setting kernel parameters]("https://help.ubuntu.com/community/GrubHowto#Setting kernel parameters")

---

### Post by user 123 on 2009-07-30
Thanks, it worked!

---

