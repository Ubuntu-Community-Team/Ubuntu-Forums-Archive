---
title: "Unsuccessful boot"
date: 2010-05-24
forum: General Help
---

### Post by n2o-Gr55 on 2010-05-24
Hi, i was playing a game on my laptop earlier this morning, (freedroid RPG) and it froze when trying to exit. This forced me to have to hold down the power button. When i attempted the restart, it did not go through, and instead produces a screen along the lines of:

fsck from util-linux-ng 2.17.2
/dev/sda1: clean,
*Starting AppArmor profiles    Skipping profile in /ect/apparmor.d/disable: usr.bin.firefox
            [OK]
*Setting sensors limits             [OK]
*Setting console screen modes and fonts

^[[7;2R

This happens every time that i try to boot. I AM able to access the terminal only mode via ctrl alt f1 though.

Additional info:
Running Lucid Lynx (RC i think)
Compaq Presario v5000

Thank you for any help you can give,
n2o-Gr55

---

### Post by arrange on 2010-05-24
It says *clean*, but I would first force check on the partition, for example via LiveCD and gParted (Partition &#8594; Check).

---

### Post by n2o-Gr55 on 2010-05-24
Trying that now, also startx returns the following

xauth: error in locking authority file /home/USERNAME/.Xauthority
xauth: error in locking authority file /home/USERNAME/.Xauthority
xauth: error in locking authority file /home/USERNAME/.Xauthority
xauth: error in locking authority file /home/USERNAME/.Xauthority

exec: 3: /usr/bin/X: not found

EDIT: doesnt look like i am getting any internet connection on it, so i cant get gParted ... :/

EDIT: Plugged it into ethernet for a sec, got gparted, when i tried to run it returns (gpartedbin:1922): Gtk-WARNING **: cannot open display:

---

### Post by arrange on 2010-05-24
It looks corrupted, LiveCD is your friend here :)

---

### Post by n2o-Gr55 on 2010-05-24
> **arrange said:**
> It looks corrupted, LiveCD is your friend here :)

Oh goodie, only a little data loss, but i loaned my liveCD to a friend >_< guess ill get started torrenting it :(

EDIT: Yet i fear i have not learned from the game, and i shall try to play it again anyway >_<


Thanks for the help anyway.

n2o-Gr55

---

