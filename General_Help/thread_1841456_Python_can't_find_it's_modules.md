---
title: "Python can't find it's modules"
date: 2011-09-09
forum: General Help
---

### Post by hutchic on 2011-09-09
Basic Problem
```
python -c "import bonobo"
Traceback (most recent call last):
  File "<string>", line 1, in <module>
ImportError: No module named bonob

```

Even though
dpkg -l | grep python-gnome2 lists it as being installed
```
ii  python-gnome2                              2.22.3-0ubuntu1
ii  python-gnome2-desktop                      2.24.0-0ubuntu1
ii  python-gnome2-dev                          2.22.3-0ubuntu1
ii  python-gnome2-extras                       2.19.1-0ubuntu11
ii  python-gnome2-extras-dev                   2.19.1-0ubuntu11

```

More Details
This has happened with a number of other python modules.  I built pygtk and a few others which had their own dependencies I had to install and build in some cases.  I'm tired of building something that is already "installed" and bonobo is being exceptionally tricky at building

```
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.10
Release:	8.10
Codename:	intrepid
Linux dcerouter 2.6.27-17-generic #1 SMP Fri Mar 12 03:09:00 UTC 2010 i686 GNU/Linux

```

I'm on 8.10 release because I'm using linuxmce and 10.04 of linuxmce is still beta.  I've already asked in linuxmce and I tried ubuntu irc but I don't see this as being a distro specific issue.

Any help would be greatly appreciated.

---

### Post by tom4everitt on 2011-09-09
So dpkg lists it as installed, but have you checked whether bonobo's actual files and folders exists/are in the right place? 

On my system, where importing bonobo works, the bonobo module folder is in /usr/lib/pymodules/python2.6/gtk-2.0. It could be worth checking that it is there, containing an __init__.py.

Either way, have you tried to reinstall the Python packages?

---

### Post by hutchic on 2011-09-09
I have tried reinstalling python

I don't have a gtk-2.0 directory in /usr/lib/pymodules/python2.6/

Moreoever I don't have a python2.5 directory in /usr/lib/pymodules/ which is what my system currently uses by default (although it looks like 2.6 is installed as well).

---

### Post by tom4everitt on 2011-09-10
Okay, then it sounds like we might have found the problem. It could of course be that python2.5 has it's modules somewhere else, perhaps in /usr/lib/python2.5, I know too little to say for sure.

But given that this folder should be there, like it is on my system, one way to try and fix this would be to simply copy this folder from a live cd, and put it in it's right place. It would probably be best with a 8.10 live cd, but it might work with a newer one also. If you don't find the folder in the live cd, I can send you mine. 

If python 2.6 is installed, you could also try to run you scripts with that one and see if it makes a difference. You just type "python2.6 program.py", instead of "python program.py". To see which version is used when you use the "python" command, do: ls -l /usr/lib/python, and check where it points.

---

