---
title: "uninstalling Python 2.5 from ubuntu 10.04"
date: 2010-07-30
forum: General Help
---

### Post by magnetpest2k7 on 2010-07-30
Hello all,

I installed python 2.5.4 from a tar file and now my pythons version has changed from 2.6 to 2.5. Can any one tell me how to uninstall from terminal? 

I am not able to find the right package name for the python 2.5

I tried sudo apt-get autoremove Python-2.5/python2.5 

Can some one  tell me how to find the exact name of the installed Python package so that i can remove it off.

Thanks

---

### Post by oldfred on 2010-07-30
You may need to be careful that you do not uninstall python. I do not know details but I think there is a link from python the the working version. Ubuntu required 2.6 to keep working so you do not want to uninstall 2.6 or if "python" is linked to 2.5 break that link before updating it.

What version do you get from just python:

fred@fred-desktop:~$ python
Python 2.6.4 (r264:75706, Dec  7 2009, 18:43:55) 
[GCC 4.4.1] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> quit
Use quit() or Ctrl-D (i.e. EOF) to exit
>>> 
fred@fred-desktop:~$ python2.5
Python 2.5.4 (r254:67916, Jan 20 2010, 21:43:02) 
[GCC 4.4.1] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>>

---

