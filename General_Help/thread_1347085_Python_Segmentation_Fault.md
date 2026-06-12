---
title: "Python Segmentation Fault"
date: 2009-12-05
forum: General Help
---

### Post by TrevT93 on 2009-12-05
Okay, so I tried to install the program Ren'Py on my laptop (running Xubuntu Karmic).  I installed the main program plus the demo then tried to execute both of them.  When I did, though, a window would pop up for a moment then disappear.  The program wouldn't actually start.  Same thing with the Demo.

My first thought was "okay, turn to Synaptic, reinstall the program."  No go; same issue.

Next was "okay, just reinstall the dependencies and then the program over again and maybe something different will happen."  Naturally, I was wrong again; I also installed a recommended dependency, but no luck.

The third thought was "okay, maybe trying to run the demo in the terminal would yield some result, which I can post in the forums."  And finally, some success!

```
trevor@TORYKTREVOR-X:/usr/share/games/renpy$ sudo ./renpy-the_question.sh
/usr/share/games/renpy/renpy/parser.py:29: DeprecationWarning: the sets module is deprecated
  import sets
/usr/share/games/renpy/renpy/script.py:31: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import md5
Fatal Python error: (pygame parachute) Segmentation Fault
Aborted 
```So...something's going wrong with Python.  Not generally a good thing, I take it.  Anyone have any ideas?

---

### Post by mc4man on 2009-12-24
Probably due to python 2.6, I guess you could file a bug (request they update to 6.10.X (no sense in offering a package(s) that don't work

see here for working sdk (in karmic
[http://renpy.org/wiki/renpy/releases/6.10.1](http://renpy.org/wiki/renpy/releases/6.10.1)

---

### Post by TrevT93 on 2009-12-24
Thanks for getting back to me.  Seems the new version does indeed work.

[Launchpad has a bug report for the exact same thing already]("https://bugs.launchpad.net/renpy/+bug/467730").  Someone from the RenPy project is already on the case.  If I'm interpreting what he's saying correctly, then a new release is in the pipeline but it won't come through that quickly because it's a universe package.

Hopefully the issue will be resolved soon for everyone, without necessitating a manual installation like I had to do.

Again, thanks!

---

