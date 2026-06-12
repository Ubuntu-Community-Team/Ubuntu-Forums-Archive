---
title: "sudo apt-get install gdesklets"
date: 2010-07-06
forum: General Help
---

### Post by kduffy101 on 2010-07-06
hi ive just run this in terminal,when i go to applications/accessories/gdesklets , a small box says starting gdesklets then it goes away.
im want to put a clock+weather temp.on my desk top.
am i doing it wrong?
cheers

---

### Post by Sanjeevtrip on 2010-07-06
try typing gdesklets on the shell prompt; and see what error it throws.

---

### Post by kduffy101 on 2010-07-06
is this what your asking me to do? im new to ubuntu,
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
kduffy101@kduffy101-desktop:~$ 
kduffy101@kduffy101-desktop:~$ gconf-editor
kduffy101@kduffy101-desktop:~$ gdesklets
Starting gdesklets-daemon...
Connecting to daemon [   ###       ]
==========================================================[07/06/10-07:38:25]===
Could not import tiling module!


Cannot establish connection to daemon: timeout!
The log file might help you solving the problem.
kduffy101@kduffy101-desktop:~$

---

### Post by Deadite81 on 2010-07-06
I tried to install gdesklets in Ubuntu 10.04 and I could not run it either.  I think gdesklets is an old project and is no longer maintained (as in zero activity for a few years...feel free to correct me if I'm wrong).

You may want to try the Screenlets program for your widget needs.

```
sudo apt-get install screenlets
```

You can find more screenlets [here]("http://gtk-apps.org/index.php?xcontentmode=6700").

---

### Post by Deadite81 on 2010-07-06
Those are the errors I received as well.  Trying to start the daemon manually wouldn't work, and I tried many other things besides...no luck.

---

### Post by Dezmond69 on 2010-07-07
> **Deadite81 said:**
> 

You may want to try the Screenlets program for your widget needs.

```
sudo apt-get install screenlets
```

You can find more screenlets [here]("http://gtk-apps.org/index.php?xcontentmode=6700").


Thanks, I had same problems with gDesklets, tried screenlets & works great.

---

### Post by groggin on 2010-07-09
OK, i have the same error, but i don't like screenlets.

  so how can we fix gdesklets?  :D

---

### Post by bnr on 2010-07-09
You can fix gdesklets with a bit o [pyhacking]("http://forum.linuxmint.com/viewtopic.php?f=90&t=32554"). Minor change to one line of python and copy a file. Confirmed fix.

---

### Post by techunit on 2010-07-09
try doing the following to fix it. 

```
sudo aptitude purge gdesklets
```

```
sudo apt-get install gdesklets
```

```
sudo aptitude show gdesklets
``` post what you get.

```
gksu gdesklets
``` sometime starting it in administrative mode helps. Don't do more than once.

```
gdesklets
```

I hope this helps... you should do this in order.

---

### Post by Meneer Jansen on 2010-07-11
Considering the fact that this is a Python app the chance that you'll run into problems is 99.9%. Python is changed (notice that I do **not** use term 'updated') every 1/2 year or so. Only problem is that it usually is **NOT** backwards compatible (now that's backwards!). Python is the the biggest piece of @$%$^@&* since the invention of the computer (yes, it is actually worse than Flash). Developers and programmers seem to think different about that because lots of applications are still being written in Py. Please stop doing that! 

If a Py app, like gDesklets, is written in Py 2.4 then chances are it won't run in Py 2.5 or higher. You''l have to install the old version next to the new. Worse than that, Ubuntu Lucid doesn't offer to install Py 2.4 anymore. And if it did you'll never know if your Py app will use the right Py version (2.4, 2.5, 2.6, 3.0: will it ever end?!).

So much for the rant, now for a summary of above mentioned solutoin.
1. Backup the troublesome file:
```
sudo cp /usr/lib/gdesklets/utils/ErrorFormatter.py  /usr/lib/gdesklets/utils/ErrorFormatter.py.orig
sudo gedit /usr/lib/gdesklets/utils/ErrorFormatter.py

```2. Change lingo of said file:
```
# 09/08/09:per  article=http://forums.opensuse.org/applications/409465-fix-gdesklets.html
#def  _new_imp(name, globs = {}, locls = {}, fromlist = []):
def  _new_imp(name, globs = {}, locls = {}, fromlist = [], test = []):

```

---

