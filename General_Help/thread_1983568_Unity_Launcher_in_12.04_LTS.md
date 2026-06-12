---
title: "Unity Launcher in 12.04 LTS"
date: 2012-05-20
forum: General Help
---

### Post by wiggly81 on 2012-05-20
ok, so i have just installed Ubuntu 12.04 and i have a problem, my unity launcher is solid grey and looks nasty, i have tried installing myunity and ccsm to adjust the transparency but it stays solid grey no matter what i do.

has anyone had this issue and is there a way to fix it?

i have GeForce 9400 GT Display Card with (Version Current) [Recommended] driver installed.

Thanx in advance :-)

---

### Post by fooman on 2012-05-20
are you currently in unity 3d or unity 2d?  ....unity 2d will not let you make many customizations.  quick way to tell which you are using:  open a terminal and type or copy/paste the following:

```
echo $DESKTOP_SESSION
```

if the resulting output says "ubuntu",  then you are using 3d and should be able to customize.

if the output says "ubuntu 2d" then you are running unity 2d.  you can switch between the 2 at the log-in screen by clicking the little * button to the right of your user name.  that will give you a drop down menu with some choices.

hope that helps.

---

### Post by wiggly81 on 2012-05-20
i had already checked this and its 3D im running

---

### Post by fooman on 2012-05-20
seems to be a bug:

[https://bugs.launchpad.net/unity/+bug/975350](https://bugs.launchpad.net/unity/+bug/975350)

---

### Post by jasonsmith01 on 2012-05-20
It effects me as well and marked as such.

---

### Post by wiggly81 on 2012-05-20
well that sux.... i guess i should get used to it till its fixed lol

---

