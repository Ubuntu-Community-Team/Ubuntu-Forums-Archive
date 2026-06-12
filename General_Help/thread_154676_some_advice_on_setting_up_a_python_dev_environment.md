---
title: "some advice on setting up a python dev environment"
date: 2006-04-03
forum: General Help
---

### Post by Choad on 2006-04-03
im wanting to learn python, so need some advice 

firstly, which ide/code editor? 

secondly, what packages do i need to install to be able to write programs in python and also i want to use opengl with python, i think there is pyopengl

its been a little while since i have used ubuntu (linux in general really) so sorry if am asking noob questions :)

also, what is the package for the ati drivers?

also also, what repositories should i add? (this is a fresh install, just ran automatix and thats about it)

---

### Post by siminone on 2006-04-03
Hi Choad to answer your  question the best I can.

I've tinkered a bit with python myself and the only IDE's I know is one called Eric and the other IDLE (I know it is python!!!). Idle is more basic with a TK interface. You can give both a try to see which one suits you most.

All packages are installed to run python (version 2.4) although you will have to install modules like python-opengl.

Not sure about ATI. Does anyone know if this is supported on Ubuntu?

The following links shows you how to add repositories 

[http://easylinux.info/wiki/Ubuntu#Repositories](http://easylinux.info/wiki/Ubuntu#Repositories)

---

### Post by Choad on 2006-04-03
cheers! python-opengl, ill remember that.

i have already broken everything tho, so it will be a while before i get back on trach (knew i shouldnt have been tempted to try and get xgl working)

"fglrx" is the driver for ati cards and i found it already so thats cool. :D

---

### Post by Choad on 2006-04-04
ok well i installed idle but it wont run

richard@ubuntu:/usr/bin$ idle-python2.4
Traceback (most recent call last):
  File "/usr/bin/idle-python2.4", line 5, in ?
    main()
  File "/usr/lib/python2.4/idlelib/PyShell.py", line 1350, in main
    root = Tk(className="Idle")
  File "/usr/lib/python2.4/lib-tk/Tkinter.py", line 1569, in __init__
    self.tk = _tkinter.create(screenName, baseName, className, interactive, wantobjects, useTk, sync, use)
_tkinter.TclError: this isn't a Tk applicationunknown color name "Black"

any ideas?

---

