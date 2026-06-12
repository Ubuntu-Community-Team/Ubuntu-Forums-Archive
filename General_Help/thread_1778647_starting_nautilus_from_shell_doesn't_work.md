---
title: "starting nautilus from shell doesn't work"
date: 2011-06-09
forum: General Help
---

### Post by wxuyec on 2011-06-09
when I type nautilus in shell and run, the nautilus doesn't start.
while I use Alt-F2 and then type nautilus, the nautilus start.
why? Thanks. my system is 10.04.

---

### Post by hakermania on 2011-06-09
There can be many reasons for this.

The most usual is that you are trying to run nautilus while being root which is not permitted :)
But it IS permitted to use
```
sudo nautilus
```But if you normally be root and try to run nautilus it won't let you

If you're sure that that's not the point, then please post the error messages you get

---

### Post by wxuyec on 2011-06-09
yes, when I use: sudo nautilus, the nautilus really start.

---

### Post by hakermania on 2011-06-09
> **wxuyec said:**
> yes, when I use: sudo nautilus, the nautilus really start.

Yes, but opening nautilus like this is dangerous because ou have root access to it and you can delete anything
When open a terminal and you give 'nautilus' without giving anything else in the terminal before that, does nautilus start?

---

### Post by wxuyec on 2011-06-09
> **hakermania said:**
> Yes, but opening nautilus like this is dangerous because ou have root access to it and you can delete anything
When open a terminal and you give 'nautilus' without giving anything else in the terminal before that, does nautilus start?
no, it doesn't start, and there is not any information printed out.

---

