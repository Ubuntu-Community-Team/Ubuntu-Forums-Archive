---
title: "Lubuntu, turn on keyboard layout changing."
date: 2012-04-07
forum: General Help
---

### Post by Aster.Orthrinos on 2012-04-07
Hi everyone! I need to turn on keyboard layout changing in Lubuntu 11.1. I know how to do this but I do not know how to make this change stay after reboot.

Here is command line I use to set Latvian and Russian changing via Shift+Alt hot-keys:

```
setxkbmap -option grp:alt_shift_toggle lv,ru
```

Now I want it to stay after reboot. I tried write this line in /etc/rc.locale but that helped me not.

---

### Post by TeoBigusGeekus on 2012-04-08
Go to ~/.config/lxsession/LXDE
Open the autostart file (create it if you don't have it) and put the command in there. Don't forget to add a & at the end, ie:
```
setxkbmap -option grp:alt_shift_toggle lv,ru &
```

---

### Post by Aster.Orthrinos on 2012-04-10
Well I had to make even lxsession and LXDE folders because I had them not but in the end it worked. Thank you!ank you!

---

### Post by TeoBigusGeekus on 2012-04-10
You're welcome and don't forget to mark the thread as solved.

---

### Post by Aster.Orthrinos on 2012-04-20
I am sorry but my problem started again. I have 

```
setxkbmap -option grp:alt_shift_toggle lv,ru &
```

in /home/username/.config/lxsession/LXDE/autostart but I cannot change layot until I launch this in terminal.

By the way how can I set thread as solved?

---

