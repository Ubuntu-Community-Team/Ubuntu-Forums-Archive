---
title: "How to install x Window System"
date: 2009-11-30
forum: General Help
---

### Post by os56k on 2009-11-30
I have Ubuntu 9.04.

I want to install a graphical program that needs X WIndows.

Actually when I execute the *make* command in program folder it gives me the following error :

"configure: error: XGAP needs XWindows X11R5 or better"

here XGAP is the name of the program.

I download source of the latest version of X Window i.e. X11R7.5 from [x.org]("http://www.x.org/releases/X11R7.5/src/") but don't know how to install it because it has more than 700 zipped files each of which haveing a *configure* and *make*.

I thought there would be X Window in Ubuntu 9.04. 
How may I know whether I have X Window in Ubuntu and if I have what version ?

---

### Post by Leppie on 2009-11-30
Ubuntu ships with the Gnome desktop environment (which depends on X, nowadays xorg).
you can check if X-windows is installed like this:
```
$which X
/usr/bin/X
$
```

---

### Post by nerdopolis on 2009-11-30
If you are already using a GUI in Ubuntu, you are probably using X .

To test for its existence (and version) run: (case sensitive)
```
Xorg -version
```I believe 9.04 has version X11R7.4 . (X11R5 came out in 1994, so there is no need to worry about the version)

If you aren't running X,
run
```
sudo apt-get install xserver-xorg
```This will use Ubuntu's packages to install X, without the need to manually compile it.
 

If X is installed, and the program is failing, then you should ask the creator of the program why its not detecting X.

---

### Post by bernt_ on 2009-12-31
> **nerdopolis said:**
> 
```
Xorg -version
```


Ubuntu karmic (9.10):
Xorg -version
...
X Protocol Version 11, Revision 0
...

---

