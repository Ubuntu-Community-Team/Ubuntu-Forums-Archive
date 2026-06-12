---
title: "How to start GUI mode in chroot environment"
date: 2010-08-31
forum: General Help
---

### Post by manishr78 on 2010-08-31
Hi All,

I am re-mastering ubuntu 9.x and not sure how do I switch to KDE mode in chroot environment.I need to edit menus and want to insert/modify few of my menus.

Does any one aware how to start GUI in chroot mode.

---

### Post by sisco311 on 2010-08-31
Hi and welcome to the forums!

You could run the apps in a nested X server. 


Start the X server from outside the chroot:
```
Xnest -ac :10.0
```

In the chroot environment set the DISPLAY variable and start a kde session:
```
DISPLAY=:10.0
startkde
```

---

### Post by manishr78 on 2010-08-31
[Thanks sisco311,]("http://ubuntuforums.org/member.php?u=244665")

I actaully dont wanna run any apps but to customize the look and feel of ubuntu.I am actually remastering backtrack DVD which is based on Ubunu and facing lot of problems, have you ever remastered any ubuntu flavor before?

---

### Post by manishr78 on 2010-08-31
By the way does that need system booted in runlevel other than 5?

---

