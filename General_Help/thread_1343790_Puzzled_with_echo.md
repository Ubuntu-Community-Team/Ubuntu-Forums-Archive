---
title: "Puzzled with echo"
date: 2009-12-02
forum: General Help
---

### Post by Kalpanaa on 2009-12-02
Hi I have a problem....Pls help me in solving this
if ABCDEF="123456"X="DEF"how do I print 123456 using X and ABC to print.Essentially, ${ABC$X} should print 123456 symbolically.No variable substitution or more lines of code is allowed.Thanks in advance,
Kalpana

---

### Post by john newbuntu on 2009-12-02
In bash:

ABCDEF="123456"
X="DEF"
eval echo \$ABC${X}

---

### Post by Kalpanaa on 2009-12-02
Many thanks :)
Kalpana

---

