---
title: "screenlets-manager won't start"
date: 2010-10-20
forum: General Help
---

### Post by Etyx on 2010-10-20
Hey guys,

I want to start using some screenlets but I'm having a few problems.

First of all, when I type "screenlets-manager" in the terminal I get this: ```
File "/usr/share/screenlets-manager/screenlets-manager.py", line 29, in <module>
    from screenlets import utils,install
ImportError: cannot import name install
```

I already checked for missing libraries using the Synaptic Package Manager and installed all needed python-libraries but I still get the same error. I also tried installing the screenlets manually by putting them into /usr/local/share/screenlets/nameofthescreenlet/screenlet.py and linking a bash file to it but nothing happened.

Any ideas how to get my screenlets running?

---

### Post by Etyx on 2010-10-20
Push

---

### Post by el_sim0n on 2010-11-20
Same terminal error and problem here. I was trying to install some new screenlets and I ended up with a screenlets manager not working. I reinstalled several times but there is no improvement - the manager starts loading and nothing appears.

---

### Post by comet7 on 2010-11-28
I had a similar problem and was able to fix it like this from the terminal:

```

screenlets

```

which allowed me to see the error:

Traceback (most recent call last):
  File "/usr/share/screenlets-manager/screenlets-manager.py", line 28, in <module>
    import screenlets
  File "/usr/lib/python2.6/dist-packages/screenlets/__init__.py", line 56, in <module>
    import menu

I then created symlinks to fix the problem(s):

```

 sudo ln -s /usr/share/pyshared/screenlets/menu.py menu.py
 sudo ln -s /usr/share/pyshared/screenlets/drawing.py drawing.py
 sudo ln -s /usr/share/pyshared/screenlets/install.py install.py

```

Hope this helps.

---

### Post by giovi81 on 2011-01-09
Thank you comet7!

I had the same problem and your tipp worked for me.

I typed "screenlets" in a terminal session and found out
the problem:

As soon as you install screenlets it asks you whether to
create folder /home/giovi/.config/autostart manually
or to let him create it for you.
If you create it manually (that was my case) do it as
NORMAL user (not root). Otherwise Screenlets won't be able
to create autostarter in it when you launch screenlets-manager!

Regards, giovanni

---

### Post by andrei90 on 2011-05-21
Greetings,

What if I have this error, how can I fix it?

```
Traceback (most recent call last):
  File "/usr/share/screenlets-manager/screenlets-manager.py", line 29, in <module>
    from screenlets import utils,install
ImportError: cannot import name install
```

---

### Post by papi on 2011-10-08
delete file /usr/local/lib/python2.7/dist-packages/screenlets:      

```
rm -r /usr/local/lib/python2.7/dist-packages/screenlets
```

This maybe solve this problem.

---

### Post by Frogs Hair on 2011-10-08
If you are using 11.04 see the link . [http://www.webupd8.org/2011/06/new-screenlets-version-014-brings.html](http://www.webupd8.org/2011/06/new-screenlets-version-014-brings.html)

---

