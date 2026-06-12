---
title: "Converting Ubuntu to Xubuntu?"
date: 2010-11-26
forum: General Help
---

### Post by The Eight-Bit Link on 2010-11-26
I would like to change my Ubuntu install to Xubuntu without having to reinstall everything or formatting my hard drive, mainly because I have XP on another partition, and I don't have the install disk for it any more (I love my XP, but not as much as Ubuntu!)
Ubuntu for me is laggier on my desktop than Xubuntu on my laptop, which is strange, but bothersome. Also, Ubuntu has a different feel that I'm not sure I like.
I would like to end up with a separate partition for GRUB, my files, Ubuntu, and XP. That way, if something screws up my Ubuntu in the future, my XP and files are fine, and my computer will still boot.

---

### Post by ivarn on 2010-11-26
```
*sudo apt*-*get install xubuntu*-*desktop* && sudo apt-get remove ubuntu desktop && sudo apt-get autoremove
```
Now do:
```
*sudo* dpkg --*configure* -a && *sudo apt*-*get* -f install *&& sudo apt*-*get* update
```

And you're done

---

### Post by eyal_allweil on 2011-05-04
Did this work? How about converting from Ubuntu Maverick to Xubuntu Natty?

---

### Post by uRock on 2011-05-04
A clean install will be much more efficient. Otherwise, run the upgrade, then install xubuntu desktop and remove ubuntu desktop.

---

### Post by The Eight-Bit Link on 2011-05-18
Sorry! Yes it did work. I'll change to [solved]

---

