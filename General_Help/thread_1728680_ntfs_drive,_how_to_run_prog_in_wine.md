---
title: "ntfs drive, how to run prog in wine?"
date: 2011-04-14
forum: General Help
---

### Post by b666 on 2011-04-14
ive got a second hard drive which is ntfs. it's got some windows programs that i'd like to run in wine. problem is i can't get "allow executing file as program" to work. when i click that, it doesn't stick.

---

### Post by TeoBigusGeekus on 2011-04-14
Wine doesn't need execution permissions for the exes to run. Just give
```
wine /path/program.exe
```
and you should be fine.

---

### Post by decrepit on 2011-04-14
Not sure about that in ubuntu.
OK in Fedora, where I ran several "dodgy" windows programs without a problem.
But ubuntu comes up with an error message saying they're not executable.
I Have the same trouble as the OP, can't get "executable" to stick.
I assume it was apparmour, being over protective.
Haven't tried disabling it to find out yet.

---

### Post by TeoBigusGeekus on 2011-04-14
Ntfs does not support linux permissions; if you want to make them executable, you have to move them to a linux file system.
But, I repeat, it shouldn't make a difference: the only program that should be executable is wine itself.

---

### Post by decrepit on 2011-04-14
I'm sure I'd done that, copied the program on CD to my home, wine wouldn't run it.
I'll have another go and see exactly what happens

---

### Post by dragonfly41 on 2011-04-14
Try right click on the *.exe and select Open in Wine loader from menu.

---

### Post by Morbius1 on 2011-04-14
> **dragonfly41 said:**
> Try right click on the *.exe and select Open in Wine loader from menu.
That won't work because that "Wine" has embedded in it something called cautious-launcher which checks to see if the exe has a linux executable bit set.

As TeoBigusGeekus pointed out, wine itself doesn't care nor can it determine if an exe has a Linux executable bit set.

---

### Post by wolfgangmcq on 2011-04-14
Wine is odd--sometimes programs will only run from the command line. If it won't run, try it from the command line. At the very least, you may get a helpful error message.

---

### Post by decrepit on 2011-04-15
yep, worked from the command line fine.

---

### Post by WorMzy on 2011-04-15
Note that you should avoid running programs stored on an NTFS partition due to limitations with the NTFS-3G driver. Small applications will probably be fine, but larger applications should be copied to a native filesystem (e.g. ext4) before running them.

---

### Post by Morbius1 on 2011-04-15
> **WorMzy said:**
> Note that you should avoid running programs stored on an NTFS partition due to limitations with the NTFS-3G driver. Small applications will probably be fine, but larger applications should be copied to a native filesystem (e.g. ext4) before running them.
Please elaborate.

---

