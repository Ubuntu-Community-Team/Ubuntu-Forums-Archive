---
title: "can not start gnome tweak tool"
date: 2012-01-16
forum: General Help
---

### Post by khaj_vah on 2012-01-16
Hello people

I have ubuntu 11.10 64bit and running gnome shell. If you ever used gnome-shell, you will know what is gnome-tweak-tool
Anyway, i can not run it. After i click on the icon, it loads few moments then stops. If i run by terminal i get this error: 

Traceback (most recent call last):
  File "/usr/bin/gnome-tweak-tool", line 22, in <module>
    import gi
ImportError: No module named gi

Please, help me :)

---

### Post by thomaslcy on 2012-01-16
I am having the same problem :( and need help as well~~

---

### Post by Xgen on 2012-01-16
First, I'll assume that you tried re-installing gnome-tweak-tool.

Try typing 'python' (without quotes) in a terminal to bring up the command interpreter. At the command line type 'import gi' and see what errors you get. One source:

[http://askubuntu.com/questions/80448/what-would-cause-the-gi-module-to-be-missing-from-python]("http://askubuntu.com/questions/80448/what-would-cause-the-gi-module-to-be-missing-from-python")

---

### Post by thomaslcy on 2012-01-16
> **Xgen said:**
> First, I'll assume that you tried re-installing gnome-tweak-tool.

Try typing 'python' (without quotes) in a terminal to bring up the command interpreter. At the command line type 'import gi' and see what errors you get. One source:

[http://askubuntu.com/questions/80448/what-would-cause-the-gi-module-to-be-missing-from-python]("http://askubuntu.com/questions/80448/what-would-cause-the-gi-module-to-be-missing-from-python")

Thanks for the reply. Here is the error message


Python 2.5.4 (r254:67916, May 24 2011, 11:02:02) 
[GCC 4.5.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import gi
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named gi
>>>

---

### Post by Xgen on 2012-01-16
As a test, what happens when you 'gksu gedit /usr/bin/gnome-tweak-tool' and comment (#) the lines 'import gi' and 'gi.require_version("Gtk", "3.0")'? Save and try gnome-tweak-tool. Reverse changes and save if no results.

---

### Post by thomaslcy on 2012-01-17
> **Xgen said:**
> As a test, what happens when you 'gksu gedit /usr/bin/gnome-tweak-tool' and comment (#) the lines 'import gi' and 'gi.require_version("Gtk", "3.0")'? Save and try gnome-tweak-tool. Reverse changes and save if no results.

gnome-tweak-tool
Traceback (most recent call last):
  File "/usr/bin/gnome-tweak-tool", line 25, in <module>
    import gtweak
ImportError: No module named gtweak

The above is the error that I got when I comment out the import gi

---

### Post by thomaslcy on 2012-01-19
I notice python2.5.4 fail to import gi while python2.7 works... my question is how can I set my default python to use python2.7 instead of python2.5???



laptop:/usr/bin$ ls -al python
lrwxrwxrwx 1 root root 18 2012-01-18 15:41 python -> /usr/bin/python2.7

laptop:/usr/bin$ ./python
Python 2.7.2+ (default, Oct  4 2011, 20:06:09) 
[GCC 4.6.1] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import gi
>>> 

laptop:/usr/bin$ python
Python 2.5.4 (r254:67916, May 24 2011, 11:02:02) 
[GCC 4.5.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import gi
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named gi
>>>

---

### Post by thomaslcy on 2012-01-19
> **thomaslcy said:**
> I notice python2.5.4 fail to import gi while python2.7 works... my question is how can I set my default python to use python2.7 instead of python2.5???



laptop:/usr/bin$ ls -al python
lrwxrwxrwx 1 root root 18 2012-01-18 15:41 python -> /usr/bin/python2.7

laptop:/usr/bin$ ./python
Python 2.7.2+ (default, Oct  4 2011, 20:06:09) 
[GCC 4.6.1] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import gi
>>> 

laptop:/usr/bin$ python
Python 2.5.4 (r254:67916, May 24 2011, 11:02:02) 
[GCC 4.5.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import gi
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named gi
>>>

Also, I figure out the system is not using the /usr/bin/python as the default python


laptop:~$ /usr/bin/python
Python 2.7.2+ (default, Oct  4 2011, 20:06:09) 
[GCC 4.6.1] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 
laptop:~$ which python
/usr/local/bin/python


so my question is how can I change it to point to the /usr/bin/python?

---

### Post by thomaslcy on 2012-01-19
OK.. finally fixed..

My workaround solution is open up the "/usr/bin/gnome-tweak-tool" in a text editor and the modify the first command from

#!/usr/bin/env python 

to

#!/usr/bin/python


and now it's using python2.7 to run this and everything seems working fine :)

---

