---
title: "Lkl and Keymap file"
date: 2006-01-23
forum: General Help
---

### Post by cholopepper on 2006-01-23
Hey guys, I've been looking around and can't seem to find the answer to this problem.
I'm currently using Kubuntu  5.10 and need to find the keymap file for my keyboard, that's cause I want to try the keylogger LKL.
Anyway, this is what I get... (I tried lots of files which I searched with "locate keymap")

unable to find keymap-file: No such file or directory
a keymap is required!! run lkl with -k <keymap>

Can anybody help me on this one?
Thanx a lot!
Javier from Argentina...

---

### Post by squidward_tentacles on 2006-05-19
Im having the exact same problem, I realize that this post is 5 months old, but no one responded.....there are so many different Keylog files, which to choose, if someone can help out with this it would be really appreciated :D

---

### Post by squidward_tentacles on 2006-05-22
anyone? <I am begining to suspect that the marked lack of response here is due others morals>

---

### Post by dgoodwin on 2006-07-19
Sorry about a late response but I if you type this: ```
lkl -l -k /usr/share/lkl/keymaps/us_km -o log.txt

``` 
Hope this helps and remember to do this as root

---

### Post by rick_1010 on 2006-10-11
Thanks, I was having the same problem too. I don't know why everyone gets so bothered by the idea of keylogging, they just assume we are trying to spy on someone but it has legitimate uses for business purposes, if someone is using a machine that you own then what is wrong with keylogging it?

---

### Post by toocrazy on 2007-05-16
Hi, any portuguese people with some pt_km* file to share ??
I dunno if this is the right place to post, sorry for that.

Cumps.

---

### Post by Bigdeath on 2008-02-21
Thanks helped me too.

---

### Post by 565Customz on 2008-06-07
where is the log file at? is say log file is log.txt but i cant find it...do i need to create it in the usr/share/lkl directory

---

