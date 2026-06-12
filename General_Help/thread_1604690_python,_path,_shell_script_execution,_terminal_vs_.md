---
title: "python, path, shell script execution, terminal vs click"
date: 2010-10-24
forum: General Help
---

### Post by mayapower on 2010-10-24
Hi,

I have created a simple python packager for *nix platform. It's working fine. In the end you have this small shell script that set some PYTHON*.* env vars and run you main script file.

When you run this script on ubuntu *hardy* either by typing it on terminal or by clicking it in file explorer, app is executing and inside my scripts, sys.executable is showing correct path.

NOTE:
run.sh, python(executable) and main.py resides in same directory.

How ever on ubuntu *karmic* the app is only executed when you run the script using terminal. If you run the shell script by clicking on it in file explorer, internally '**sys.executable**' is always showing '***home/<user>/Docments/***', which is not the correct path.

I tried other method also by using python's *__file__* variable but it's also showing the same fixed path as mentioned above.

I am not that much familiar with linux internals and this is some thing to do with the OS rather then python problem.

I don't how this script is going to behave on other *nix flavors?

Any pointers?

Cheers

Prashant

---

