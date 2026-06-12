---
title: "can't tell which python version I have"
date: 2011-05-02
forum: General Help
---

### Post by now0pen on 2011-05-02
> jimsyyap@jimsyyap-desktop:~$ python -V
Python 2.7.1+
jimsyyap@jimsyyap-desktop:~$ python3
Python 3.2 (r32:88445, Mar 25 2011, 19:28:28) 
[GCC 4.5.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> It seems I have python 3.2 installed (correct?), how come when I type in 'python -V it still shows python 2.7.1? Do I have to remove that (using synaptic)?

Thanks!

---

### Post by 3rdalbum on 2011-05-02
> **now0pen said:**
> It seems I have python 3.2 installed (correct?), how come when I type in 'python -V it still shows python 2.7.1? Do I have to remove that (using synaptic)?

Thanks!

No! Do NOT remove Python 2.

The Ubuntu system still depends on Python 2, and a lot of Python programs require Python 2 as well. This is why 'python' links to Python 2, not 3.

If you need to use 3, then run 3 explicitly, and put python3 in the shebang at the top of your script.

---

