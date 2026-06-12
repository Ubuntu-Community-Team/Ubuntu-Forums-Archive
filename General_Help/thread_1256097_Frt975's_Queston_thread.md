---
title: "Frt975's Queston thread"
date: 2009-09-02
forum: General Help
---

### Post by frt975 on 2009-09-02
[LIST=1]
[*][COLOR=Red]**[SOLVED]**[/COLOR] When I boot ubuntu the first half of usplash works, but after that it shows me the all the text such as "Reading files needed to boot    [OK]".How do I make usplash go all the way end.
[*]How can I get the advanced window features in kwin to metacity?
[*][COLOR=Red]**[SOLVED]**[/COLOR]I was messing around with my /usr/share/icons dictionary. I have 3 partitions: / ,/usr ,/home.
[*]My sound isn't working.
[/LIST]

---

### Post by P4man on 2009-09-02
1. try this:
```
sudo update-alternatives --config usplash-artwork.so
```
also make sure you have  "quiet splash" at the end of your kernel parameters in grub.

2. depends what features you are thinking about, but probaly, no, you can't. Unless you mean the kwin effects, which can be configured in compiz. Install compizconfig-settings-manager and eat your heart out ;)

---

### Post by frt975 on 2009-09-02
> depends what features you are thinking about, but probaly, no, you can't. Unless you mean the kwin effects, which can be configured in compiz. Install compizconfig-settings-manager and eat your heart out I'm thinking of the no task-bar icon, no border, and fixed geometry.

---

### Post by frt975 on 2009-09-18
Added question 3

---

### Post by frt975 on 2009-09-19
Reinstall fixed 1 & 3 but broke sound. :(:confused:

---

