---
title: "force quit"
date: 2009-08-01
forum: General Help
---

### Post by volter on 2009-08-01
Some times I have some problems that the program not responding. How can wrap the the window (like in Windows alt+f4 / Ctrl+Esc), to make force quiting. 
help me?!!!!?!?!?!

---

### Post by f37u5g0d on 2009-08-01
I don't really know what you mean by "wrap the window," but you can use the force quit applet on the gnome panel.  Typically if an application is not responding if you right click the title bar you can click "close" and the force quit dialog will open but not always.  Lastly simply open up the "System Monitor" find the process and right click -> kill it.

---

### Post by SPr on 2009-08-01
alt+ctrl+f1 or open a terminal.
```

pidof hung_program_name

```
returns a number which can be used
```

kill number_returned_by_pidof

```
If that doesn't work try sending different signals. [This](http://linux.about.com/od/bgb_guide/a/gdebgb87t01.htm) is nice write up of the various signals and which ones to use and why.

See also killall

---

### Post by alexandari on 2009-08-01
yea that`s another fast solution

alt+f2

killall (program name)

---

### Post by volter on 2009-08-01
> **SPr said:**
> alt+ctrl+f1 or open a terminal.
```

pidof hung_program_name

```
returns a number which can be used
```

kill number_returned_by_pidof

```
If that doesn't work try sending different signals. [This](http://linux.about.com/od/bgb_guide/a/gdebgb87t01.htm) is nice write up of the various signals and which ones to use and why.

See also killall

thnx man, but how can I open terminal if alt+ctrl+f1 doesn't work?

---

### Post by Lavaeagle on 2009-08-01
Or you could go easy on yourself grab the "Force Quit" application and shortcut it to your task bar on top and use that to just click the window and it will shut it down.

---

### Post by SPr on 2009-08-01
It's easier but if the mouse has hung...

---

### Post by SPr on 2009-08-01
> **volter said:**
> thnx man, but how can I open terminal if alt+ctrl+f1 doesn't work?

There will be a link to a terminal in the menu or if that isn't accessible and alt+ctrl+f1 to f6 doesn't work then you can try logging out and back in. If you can't logout using the GUI try ctrl+backspace.

If you can't log out or the system isn't responding at all try
Ctrl + Alt + SysRq + R
followed by E,I,S,U and B (BUSIER spelt backwards).
That will reboot the PC in a nice and safe manner.

---

