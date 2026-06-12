---
title: "Clementine won't open"
date: 2011-09-15
forum: General Help
---

### Post by geo909 on 2011-09-15
Hi all,

I just installed lubuntu 11.04, everything is fine except
that Clementine does not open at all. Below you can find 
the error message that I get when I run it from a terminal.

Do you have any idea why this is happening? Could somebody
please help?

Thanks a lot in advance..

Here is the error message (clementine never opens)

```

jorge@Office-Desktop:~$ clementine 
Couldn't load icon "clementine-panel" 
Couldn't load icon "clementine-panel-grey" 
Error connecting to notifications service. 
virtual bool GnomeGlobalShortcutBackend::DoRegister() - starting 
virtual bool GnomeGlobalShortcutBackend::DoRegister() - gnome settings daemon not registered 
virtual bool QxtGlobalShortcutBackend::DoRegister() 
Couldn't load icon "find" 
Application asked to unregister timer 0x1f00000a which is not registered in this thread. Fix application.
Bus error
jorge@Office-Desktop:~$ 

```

---

### Post by dniMretsaM on 2011-09-15
Have you tried reinstalling? It looks to me that it might be missing some dependencies or something (take this with a grain of salt because I really have no idea, but give it a shot anyway). Someone smarter will probably be able to give you a better answer.

---

### Post by geo909 on 2011-09-15
Thanks but this doesn't work.. I did 
```
sudo apt-get purge clementine
```
even erased the folder "Clementine" under ~/.config but I get the same error..

---

### Post by geo909 on 2011-09-18
bump?!

---

### Post by geo909 on 2011-09-20
Nobody?

---

### Post by geo909 on 2011-09-21
:cry:

---

### Post by TedN on 2011-09-22
> **geo909 said:**
> Hi all,

I just installed lubuntu 11.04, everything is fine except
that Clementine does not open at all. Below you can find 
the error message that I get when I run it from a terminal.

Do you have any idea why this is happening? Could somebody
please help?

Thanks a lot in advance..

Here is the error message (clementine never opens)

```

jorge@Office-Desktop:~$ clementine 
Couldn't load icon "clementine-panel" 
Couldn't load icon "clementine-panel-grey" 
Error connecting to notifications service. 
virtual bool GnomeGlobalShortcutBackend::DoRegister() - starting 
virtual bool GnomeGlobalShortcutBackend::DoRegister() - gnome settings daemon not registered 
virtual bool QxtGlobalShortcutBackend::DoRegister() 
Couldn't load icon "find" 
Application asked to unregister timer 0x1f00000a which is not registered in this thread. Fix application.
Bus error
jorge@Office-Desktop:~$ 

```
________________________________________

I have a similar problem. {new installation of Ubuntu 11.04} Clementine actually worked when I installed it from the software center, but the next day it wouldn't launch at all. Uninstalling and reinstalling doesn't help. Uninstalling Banshee doesn't help. The Clementine site:
[http://code.google.com/p/clementine-...detail?id=1976](http://code.google.com/p/clementine-...detail?id=1976)
 says this is a known problem with Ubuntu, but implies it is related to Unity. I am using Classic, and still have the problem. I only had one evening with Clementine, and I fell in love and now it's gone! Can anyone help.

---

### Post by geo909 on 2011-09-23
> 
I have a similar problem. {new installation of Ubuntu 11.04} Clementine actually worked when I installed it from the software center, but the next day it wouldn't launch at all. Uninstalling and reinstalling doesn't help. Uninstalling Banshee doesn't help. The Clementine site:
[http://code.google.com/p/clementine-...detail?id=1976](http://code.google.com/p/clementine-...detail?id=1976)
says this is a known problem with Ubuntu, but implies it is related to Unity. I am using Classic, and still have the problem. I only had one evening with Clementine, and I fell in love and now it's gone! Can anyone help.


Thanks for the heads up! That's definitely not a unity-related problem, I'm using native lxde (just openbox)..

Btw your link is dead..

---

### Post by Bruno Koop on 2011-11-07
Hi!

Does anyone have a solution to this problem?

I got clementine working on my laptop (ubuntu 11.10), but it doesn't run on my desktop pc (lubuntu 11.10). So I can confirm that it's not a Unity problem.

Thanks for help!
Bruno

---

### Post by waterscribe on 2011-12-17
This solution worked for me - 

**Source:** [http://code.google.com/p/clementine-player/issues/detail?id=2327](http://code.google.com/p/clementine-player/issues/detail?id=2327)

> This is a bug in the qt-at-spi package.  Here's the upstream bug: [https://bugs.launchpad.net/ubuntu/+source/qt-at-spi/+bug/875661](https://bugs.launchpad.net/ubuntu/+source/qt-at-spi/+bug/875661)  To work around it you can turn off the universal access settings in gnome, or remove the qt-at-spi package.         

i.e.
```
sudo apt-get remove qt-at-spi
```

---

