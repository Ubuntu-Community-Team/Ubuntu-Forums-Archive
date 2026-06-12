---
title: "QtCreator starts very slowly and eats CPU"
date: 2010-07-19
forum: General Help
---

### Post by skywriter on 2010-07-19
The same bug as described [_here_](http://ubuntuforums.org/showthread.php?t=1441720). After waiting for several minutes QtCreator starts but after restarting it the issue repeats again.

The option "-noload Help" helps, but it seems as a temporary workaround rather then stable solution.

Is there any stable solutions?

I'm using Ubuntu 10.04, QtCreator 1.3.1.

---

### Post by skywriter on 2010-07-21
Is it really nobody uses QtCreator with 10.04?

---

### Post by Vaphell on 2010-07-21
i used it few times but had no issues whatsoever, tested 1 minute ago - everything's still fine. But i have qt4.6.2-0 and this bug affects 4.6.2-1

---

### Post by Kerubu on 2010-07-25
This occured with me also under 10.04. QTCreator took an age to start. 
Then all of a sudden it started up fine, no long pause and I didn't alter anything !

I have now just installed 10.04 on another laptop and again it gets a long delay starting qtcreator

---

### Post by Kerubu on 2010-07-25
> **skywriter said:**
> The same bug as described [_here_](http://ubuntuforums.org/showthread.php?t=1441720). After waiting for several minutes QtCreator starts but after restarting it the issue repeats again.

The option "-noload Help" helps, but it seems as a temporary workaround rather then stable solution.

Is there any stable solutions?

I'm using Ubuntu 10.04, QtCreator 1.3.1.

I just discovered the way to stop it taking an age to start up:

Start it up as normal

Go to the Help tab on the left and browse the help pages for a while.. any pages will do.

Shutdown Qtcreator

Restart it.. should take seconds now.

---

