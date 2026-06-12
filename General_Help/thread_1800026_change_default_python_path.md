---
title: "change default python path"
date: 2011-07-08
forum: General Help
---

### Post by qingkunl on 2011-07-08
Does anybody know how to change the path for python? Like, for now, the default path is /usr/bin/python, how can manually I change it to /usr/local/bin/python?

---

### Post by Bachstelze on 2011-07-08
Let me guess, you installed a Python version from source and what to use it when you type "python" in a shell? Define an alias like

```
alias python="/usr/local/bin/python"
```

---

### Post by adit on 2011-07-08
The answer is you can not change it (what is already installed in /usr/bin directory).  The only way is install python in a different directory and add that directory to the PATH environment variable.
First test value of your PATH environment variable.  In a default ubuntu installation
```
:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```
The solution is install (another instance of) python to /usr/local/bin (in addition to the default python installation).  When you type python in terminal /usr/local/bin/python will be called first.  If /usr/local/bin/python is not found in your system, then the default /usr/bin/python will be called.

---

