---
title: "Is it possible to move Windows to another hard drive ?"
date: 2011-02-23
forum: General Help
---

### Post by mrpenguin on 2011-02-23
I am buying a new laptop and of course it comes with Windows 7, I prefer not dual booting and want to keep windows on a separate hard drive for that once in a blue moon I need windows, the hard drive is pretty sweet and I would rather use the new hard drive for Ubuntu and put windows on a smaller slower drive.
The laptop obviously dont come with the Windows CD

Is it possible to move the entire hard drive to another hard drive ??

---

### Post by jnguyen on 2011-02-23
Yes. There are several ways to do it, but I like Ghost Image the best.
jvn

---

### Post by asmoore82 on 2011-02-23
Yes, Clonezilla! [http://clonezilla.org/](http://clonezilla.org/)

You can even move it to a smaller hard drive. Just shrink it first with
GParted, check the disk natively (in Windows) to make sure the shrink
caused no problems, then clone it to the smaller drive.

---

### Post by mrpenguin on 2011-02-23
Nice ! Thanks
So it will even clone Windows itself so that it dont even know its on a different hard drive ?

---

### Post by asmoore82 on 2011-02-24
Windows will *"know"* it's own a different hard drive but from a technical
standpoint it will still work fine within the same computer. Now from a
licensing standpoint, post-XP Windows may require and/or refuse re-activation.

---

### Post by mrpenguin on 2011-02-24
Thank you for the info

---

