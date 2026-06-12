---
title: "Printer dialogue box"
date: 2010-09-24
forum: General Help
---

### Post by bilal_pieas on 2010-09-24
Hi Everyone,

I have this strange problem of not being able to open the printer dialogue box. When i go to system->administration->printing, the system shows a busy sign for a few seconds and then nothing happens after that. Is there any one who can help me out. 

Thanks
bilal

---

### Post by sikander3786 on 2010-09-24
Hi and welcome to the forums. :-)

Type the following command in a terminal and post any error message reporter there.

```

system-config-printer

```

Irrespective of that, which printer are you using?

---

### Post by bilal_pieas on 2010-09-24
i get the following 

[B]Traceback (most recent call last):
  File "/usr/share/system-config-printer/system-config-printer.py", line 31, in <module>
    from timedops import *
  File "/usr/share/system-config-printer/timedops.py", line 20, in <module>
    import gobject
ImportError: No module named gobject[/B]

---

### Post by sikander3786 on 2010-09-24
Which version of Ubutnu are you using? Did you install some other version of python in addition to the default one? Type **python** in a terminal and post the output. Use ctrl + D to exit the >>> prompt after you are done.

---

### Post by bilal_pieas on 2010-09-24
Thanks for your reply. Yes i did install Python 2.7. Actually i wanted to install 3d software blender and read somewhere that it needs Python. But I didn't know that Python is very deep roots in Linux and is already installed. sorry for not being able to post the output as you suggested now because i am not sitting on the same computer. I shall post it as soon as possible. 
Thanks again
 
Bilal

---

### Post by sikander3786 on 2010-09-25
> 

I found the solution to this on my system.

I had installed a non-ubuntu distribution of python (stackless python). This became the default python installation used by the system, but was located in /usr/local/bin/python not /usr/bin/python, so the path to all the other modules was wrong.

To fix, I renamed the stackless python version from /usr/local/bin/python to /usr/local/bin/spython. I now have 2 python installations and the system picks up the default installation. Perfect.


A solution from a similar bug page. See the related bug page for more details.

[https://bugs.launchpad.net/ubuntu/+bug/210738](https://bugs.launchpad.net/ubuntu/+bug/210738)

---

### Post by bilal_pieas on 2010-09-25
Yes it did work for me. Thanks a lot. I can now see my printer dialogue box again.

Bilal

---

