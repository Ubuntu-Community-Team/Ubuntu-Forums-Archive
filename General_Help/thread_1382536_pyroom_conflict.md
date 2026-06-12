---
title: "pyroom conflict"
date: 2010-01-16
forum: General Help
---

### Post by namluc on 2010-01-16
Pyroom stopped working on my other install a while ago, so i have just reinstalled karmic just to get it working. after using the computer for a day it has stopped working again

```

luke@luke-laptop:~$ pyroom
Traceback (most recent call last):
  File "/usr/bin/pyroom", line 35, in <module>
    import sys, PyRoom.cmdline
  File "/usr/lib/python2.6/dist-packages/PyRoom/__init__.py", line 34, in <module>
    fallback=True)
  File "/usr/lib/python2.6/gettext.py", line 480, in translation
    mofiles = find(domain, localedir, languages, all=1)
  File "/usr/lib/python2.6/gettext.py", line 437, in find
    for nelang in _expand_lang(lang):
  File "/usr/lib/python2.6/gettext.py", line 132, in _expand_lang
    locale = normalize(locale)
  File "/usr/lib/python2.6/locale.py", line 333, in normalize
    fullname = localename.lower()
AttributeError: 'list' object has no attribute 'lower'

```

both versions 3.x and 4.x were all working until today, very annoying, this is the same message as in my old installation

thanks in advance for help:D

---

### Post by U_Academical on 2010-01-16
[https://bugs.launchpad.net/pyroom/+bug/365477](https://bugs.launchpad.net/pyroom/+bug/365477)  This bug had been documented, one suggested work around is to download and reinstall PyRoom from its website.  [http://pyroom.org/download.html](http://pyroom.org/download.html)  Word is its been fixed but it just takes a while for Fixes to make it into the package tree.

---

### Post by tiax on 2010-01-16
Hi,

PyRoom dev here. I'm sorry this bug still persists, it's actually fixed upstream but we haven't made a new release since. It's got to do with locales.. I'll see if we can make a new release soon and upload packages to our PPA.

Cheers

---

### Post by namluc on 2010-01-16
tiax and u_academical

thanx for the swift replies, I just grabbed the tarball from the /downloads section of your website, unfortunately the result was the same:

> 
luke@luke-laptop:~/Downloads/pyroom-0.4.1$ ./pyroom
Traceback (most recent call last):
  File "./pyroom", line 35, in <module>
    import sys, PyRoom.cmdline
  File "/home/luke/Downloads/pyroom-0.4.1/PyRoom/__init__.py", line 34, in <module>
    fallback=True)
  File "/usr/lib/python2.6/gettext.py", line 480, in translation
    mofiles = find(domain, localedir, languages, all=1)
  File "/usr/lib/python2.6/gettext.py", line 437, in find
    for nelang in _expand_lang(lang):
  File "/usr/lib/python2.6/gettext.py", line 132, in _expand_lang
    locale = normalize(locale)
  File "/usr/lib/python2.6/locale.py", line 333, in normalize
    fullname = localename.lower()
AttributeError: 'list' object has no attribute 'lower'
luke@luke-laptop:~/Downloads/pyroom-0.4.1$ 


any suggestions?

---

### Post by villon on 2010-01-22
Hi namluc,

I met this problem when changed my desktop language from English to Hungarian. Googling the error message found the bug U_Academical already reffered to. Here at comment #12 [ [https://bugs.launchpad.net/pyroom/+bug/365477/comments/12](https://bugs.launchpad.net/pyroom/+bug/365477/comments/12) ] they say the bug could be reproduced by setting a value to the LANGUAGE environment variable.

I echoed the variable in terminal, and it had a value so I get rid of it.

So my solution was to add a 

LANGUAGE=

line to the .profile file in my home folder, logout then login, and now all seems to be working. I don't know if this will mess up anything else with my system or other applications in the future.

Before editing .profile you can try setting LANGUAGE in terminal and then run pyroom also from terminal to see if it works.

---

### Post by namluc on 2010-03-01
only just seen your reply!

what would be the exact launch code from the terminal including that language option?

cheers!

---

### Post by namluc on 2010-03-01
bump

---

### Post by namluc on 2010-03-02
bump

---

### Post by namluc on 2010-03-03
bump

---

### Post by ein anderer on 2010-06-01
just type 
[FONT=Fixedsys]LANGUAGE=[/FONT]
in the terminal.
(this is not permanent!)

i had the same bug and it works now.

---

