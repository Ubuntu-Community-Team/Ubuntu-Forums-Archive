---
title: "progname = ; ARGB=on;"
date: 2010-07-29
forum: General Help
---

### Post by cam888 on 2010-07-29
Lately I installed a new theme engine for gtk, murrine, and gnome-color-chooser, where I set murrine as the global engine, and set ARGB to be true. Since then some applications (emacs23 and eclipse) have stopped working, and whenever I execute a program from command line, the following gets printed before the window appears:
```

cameron@cameron-laptop:~$ gnome-calculator 

progname=gnome-calculator; RGBA=on

```

For the programs that exit, they open a window, and then very soon afterwards, recieve an X protocol error: BadMatch, and quit after that.
```

cameron@cameron-laptop:~$ emacs23

progname=emacs23; RGBA=on
X protocol error: BadMatch (invalid parameter attributes) on protocol request 2

```

I have tried setting the global engine to be something else, and tried to disable ARGB, but nothing is working. Currently gnome-color-chooser reports mist to be the global theme engine.

I hope somebody can help me understand what is going on, I'd like to be able to use emacs again!

Thanks.

---

### Post by stinkeye on 2010-07-29
Have a look at this blog which explains how to write a couple of lines to your ~/.profile file to disable rgba for certain apps.
Also explains how to revert the changes made by enabling rgba transparency if your still having trouble.
[**_[COLOR="DarkRed"]http://www.webupd8.org/2010/05/enable-rgba-transparency-in-ubuntu-910.html[/COLOR]_**]("http://www.webupd8.org/2010/05/enable-rgba-transparency-in-ubuntu-910.html")

---

### Post by cam888 on 2010-07-29
That worked excellently. Both emacs and eclipse now work, and the string has stopped being displayed.

Thank you very much.

---

