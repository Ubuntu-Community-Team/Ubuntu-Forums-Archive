---
title: "Applications not starting, Python issue"
date: 2011-02-10
forum: General Help
---

### Post by Sansari on 2011-02-10
Running Xubuntu 10.04 64-bit on a partition w/ no swap space partition (shouldn't be relevant)

Some of my applications are acting strangely. My main issue is that Blender won't  start up anymore. I'm not sure what happened to cause it, since I didn't change any blender-related files between the time when it was working and when it wasn't working. If I try to open it now, the window pops up for an instant  and closes immediately. I tried running it through the terminal and got this message.

~$ blender
found bundled python: /opt/blender-2.56a-beta-linux-glibc27-x86_64/2.56/python
Fatal Python error: Py_Initialize: can't initialize sys standard streams
Traceback (most recent call last):
  File "/usr/lib64/python2.6/encodings/utf_8.py", line 9, in <module>
  File "/usr/lib64/python2.6/codecs.py", line 16
    except ImportError, why:
                      ^
SyntaxError: invalid syntax
Aborted


If I'm not mistaken, Blender 2.5 is supposed to use a bundled python 3 instead of the installed python 2.6.5. Other applications are facing trouble too. For example, Compiz is working fine, but I can't open the compizconfig settings manager. I can run compiz --replace through the alt+f2 run command, but when I do so through the terminal, it gets stuck and doesn't complete the restart, so I have to ctrl+C. Compiz is written in C but can use python scripts, so that may be the problem.

I don't know what's wrong, but I'm sure it's related to python.
Also, I installed Blender with these instructions:
[http://wiki.blender.org/index.php/Doc:Manual/Introduction/Installing_Blender/Linux](http://wiki.blender.org/index.php/Doc:Manual/Introduction/Installing_Blender/Linux)
replacing 2.49 w/ 2.56a, of course, but that means I must have directed Blender to the 2.6.5 version of python... It was working initially, but I tried opening it later and got the error.
I deleted the last bit of those instructions (in the /etc/profile file), but I'm still getting the same error.
I think I may just reinstall Xubuntu entirely since I don't have much on this partition right now, but I definitely still want to know what's wrong with my current setup.
So... Help?

---

### Post by Sansari on 2011-02-11
Any help? I'd really like to know what's crippling my OS...

---

