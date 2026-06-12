---
title: "Messed up start up programs"
date: 2010-12-11
forum: General Help
---

### Post by clint8679 on 2010-12-11
Hi - So I am new to ubuntu and loving it but today did something silly.  I decided to stop some programs on start up (something i learnt to do in windows to speed things up). I also deleted compiz (accidently)

I've mananaged to mess things up.  On re-boot I can not see any minimise, close, expand buttons on the top of windows. I've reinstalled compiz but still having the problem.  

Happy to reinstall ubuntu if necessary, but dont know how exactly.  But suspect its not necessary.

Would appreciate any help

---

### Post by karthick87 on 2010-12-11
Have you enabled compiz in your startup applications??

---

### Post by clint8679 on 2010-12-11
No - can you let me know how to do that?

---

### Post by oldos2er on 2010-12-11
Open a terminal (Applications, Accessories, Terminal), and run ```
metacity --replace
```

---

### Post by clint8679 on 2010-12-11
Thanks.  But still have the same problem.  For example, in rhythm box, there is no buttons to close or minimise at all so cant close the program.  Other apps I have to close from the file menu

---

### Post by karthick87 on 2010-12-11
Reset compiz settings to default and the reboot your system.

```
gconftool-2 --recursive-unset /apps/compiz
```

---

