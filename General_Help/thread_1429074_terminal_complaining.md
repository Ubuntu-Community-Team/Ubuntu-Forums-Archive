---
title: "terminal complaining"
date: 2010-03-13
forum: General Help
---

### Post by JcZndeR on 2010-03-13
Recently I have discovered that while using the the command line, I'll mistype something and the terminal spews out some traceback and seems to complain about CommandNotFound
I have never noticed this before
is this normal?
```

ubuntu:~$ sud
Traceback (most recent call last):
  File "/usr/lib/command-not-found", line 8, in <module>
    import CommandNotFound
  File "/usr/lib/python2.6/dist-packages/CommandNotFound/__init__.py", line 1, in <module>
    from CommandNotFound import CommandNotFound
  File "/usr/lib/python2.6/dist-packages/CommandNotFound/CommandNotFound.py", line 4, in <module>
    import sys, os, os.path, gdbm, posix, grp, string
ImportError: /usr/lib/python2.6/lib-dynload/gdbm.so: invalid ELF header

```

---

### Post by dcstar on 2010-03-13
> **JcZndeR said:**
> Recently I have discovered that while using the the command line, I'll mistype something and the terminal spews out some traceback and seems to complain about CommandNotFound
I have never noticed this before
is this normal?
.......

No it is not normal, if you type in a bad command there is a script that is supposed to run that gives you a list of possible commands that you may have misspelt (at least it does in 10.04 Alpha).

---

### Post by JcZndeR on 2010-03-14
mm, I agree..
I do believe that IS the script
but failing, quite badly, or rather the execution of the script failing

---

### Post by dcstar on 2010-03-14
> **JcZndeR said:**
> mm, I agree..
I do believe that IS the script
but failing, quite badly, or rather the execution of the script failing

Create a new user and see if the problem is there, if it isn't then you have corrupted your original profile somewhere.

If it is still there then a system package/configuration is probably broken.

---

