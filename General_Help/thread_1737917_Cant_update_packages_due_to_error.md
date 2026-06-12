---
title: "Cant update packages due to error"
date: 2011-04-24
forum: General Help
---

### Post by LatinaLover93 on 2011-04-24
E: Type 'ain' is not known on line 3 in source list /etc/apt/sources.list.d/gnome3-team-gnome3-natty.list
E: The list of sources could not be read.
 i get this error when i try to update my packages, anybody know a fix?

---

### Post by plucky on 2011-04-24
> **LatinaLover93 said:**
> E: Type 'ain' is not known on line 3 in source list /etc/apt/sources.list.d/gnome3-team-gnome3-natty.list
E: The list of sources could not be read.
 i get this error when i try to update my packages, anybody know a fix?

Why is your thread have the [Solved] in the title?

Open a terminal and post output of ```
cat /etc/apt/sources.list.d/gnome3-team-gnome3-natty.list
```

---

### Post by .ringaila on 2011-05-08
I don't know why this happened. But this should help:
1. login as root in order to to edit root files:
```
sudo -i
```
2.open  gnome3-team-gnome3-natty.list file using any text editor you want(i used pico)
```
pico /etc/apt/sources.list.d/gnome3-team-gnome3-natty.list

```
3. delete 'ain' in line 3 and save the changes.

---

### Post by runesvend on 2011-07-14
You're experiencing [Bug #789859]("https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/789859"):

If you're interested in getting this fixed, please mark this bug as affecting you on the following page:

[https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/789859]("https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/789859")

---

### Post by joy_live on 2012-08-14
> **.ringaila said:**
> I don't know why this happened. But this should help:
1. login as root in order to to edit root files:
```
sudo -i
```
2.open  gnome3-team-gnome3-natty.list file using any text editor you want(i used pico)
```
pico /etc/apt/sources.list.d/gnome3-team-gnome3-natty.list

```
3. delete 'ain' in line 3 and save the changes.

Thanks man, it works!

---

