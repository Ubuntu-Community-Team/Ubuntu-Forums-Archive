---
title: "32 bit compatibility library - how to?"
date: 2009-09-13
forum: General Help
---

### Post by mac666 on 2009-09-13
Hey
i used **sudo apt-get install ia32-libs** , but it tells me that i allready have it up to date.
but it doesnt work;

```

mac@turd:~/Downloads/lampp$ sudo ./lampp 
XAMPP is currently only availably as 32 bit application. Please use a 32 bit compatibility library for your system.

```

Any hint? :S

---

### Post by Vaphell on 2009-09-13
[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

### Post by binh0 on 2012-01-03
I had the same problem on my hp ProBook 4530s.
As it turns out, the solution was to install ia32-libs-multiarch:i386 instead of ia32-libs.

---

### Post by oldos2er on 2012-01-03
Closed, necromancy.

---

