---
title: "Live CD help"
date: 2009-10-28
forum: General Help
---

### Post by Bearded-flower on 2009-10-28
my ubuntu partition died. error 15. i have tried everything i can think of, and everything i can find on the forums. i have given up.
BUT i have a alot of graphics work, and music and photos i need to keep.
but i cant access them on tjhe live CD. i cant view. move. copy. nothing.
how do i get it so can copy this stuff to my win7 partition?

---

### Post by Bearded-flower on 2009-10-28
B to the U to the M to the P

---

### Post by community nerd on 2009-10-28
When I had a system crash I just booted from a puppylinux usb drive and pulled stuff off it. How is it not letting you get it with the livecd. It wont let you boot or what?

---

### Post by Bearded-flower on 2009-10-28
i boot into the live CD fine. i find the files fine. but cos my profile was set to privtae i cant touch them. i can see them but thats it.

---

### Post by theozzlives on 2009-10-28
you can hit alt+F2 and type:
```
gksu nautilus
```
copy the files that way.

---

### Post by Bearded-flower on 2009-10-28
Nice tat, oh and what? ok, i know what alt F2 does, but when i use "gksu nautilus" then what? do i "gksu /usr/... whatever/img.jpg ?

---

### Post by fluffman86 on 2009-10-28
no, gksu nautilus lets you run the file browser as root.  So press alt+f2 and type gksu nautilus, then do that again.  In one file browser, go to your old /home directory, copy your files, and paste them onto your external media on the other.

---

### Post by Bearded-flower on 2009-10-28
Kay, thanks.

---

