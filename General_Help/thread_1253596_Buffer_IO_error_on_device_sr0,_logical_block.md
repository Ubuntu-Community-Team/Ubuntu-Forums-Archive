---
title: "Buffer I/O error on device sr0, logical block"
date: 2009-08-30
forum: General Help
---

### Post by Deatzo Seol on 2009-08-30
Hey everyone

I have these freakishly frequent errors on the tty (which is quite disturbing, as it clutters it and ssh becomes almost unusable):
> 
Buffer I/O error on device sr0, logical block 0
Buffer I/O error on device sr0, logical block 1
Buffer I/O error on device sr0, logical block 2
Buffer I/O error on device sr0, logical block 3
etc


As far as my knowledge goes, sr0 is supposed to be a CDROM drive. However, I only have this error when no CD is inserted.

On the other hand, when I do insert a CD, the error message stops, but a new one pops up (though only once every five minutes or so):
> Uhhuh. NMI received for unknown reason b1 on CPU0.
You have some hardware problem, likely on the PCI bus.
Dazed and confused, but trying to continue.

So now... this error really sucks, as I almost always use a tty...

Solutions? Please?

---

### Post by Liolikas on 2009-08-30
I remember I had same error when I inserted broken CD (broken I mean almost with 2 holes instead one).

---

### Post by P4man on 2009-08-30
I've seen it once on a machine with an overheating cpu. 
thats not to say you're having the same, but I did find it a funny but not very helpful error msg :)

---

