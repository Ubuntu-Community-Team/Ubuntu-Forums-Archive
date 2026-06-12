---
title: "Terminal not opening"
date: 2012-05-18
forum: General Help
---

### Post by praveenkumarpon on 2012-05-18
Hi,
The Terminal in Unity is not opening. It shows in the taskbar that it is opening it, and then nothing. I tried it in Gnome too.

Its working in the Guest account. Also Xterm is working in my user account. Is there a way to bring it back?

---

### Post by 0011235813 on 2012-05-18
> **praveenkumarpon said:**
> Hi,
The Terminal in Unity is not opening. It shows in the taskbar that it is opening it, and then nothing. I tried it in Gnome too.

Its working in the Guest account. Also Xterm is working in my user account. Is there a way to bring it back?

Try installing a different terminal?

---

### Post by praveenkumarpon on 2012-05-18
> **0011235813 said:**
> Try installing a different terminal?

I removed the default terminal and installed it again, the same problem continues. Xterm and Uxterm are working fine.

Iam new to Ubuntu and only know to do some simple sh and c programs in the terminal.

Its still not opening.

---

### Post by drs305 on 2012-05-18
Since a different user's terminal is working ok, try renaming your gnome-terminal config folder: ~/.gconf/apps/gnome-terminal
I usually just add an 'x' to the end, but rename it anything you want.

Then try opening the terminal again. It should create a new gnome-terminal folder, and if the error is within the original, terminal should now open.

---

### Post by praveenkumarpon on 2012-05-18
> **drs305 said:**
> Since a different user's terminal is working ok, try renaming your gnome-terminal config folder: ~/.gconf/apps/gnome-terminal
I usually just add an 'x' to the end, but rename it anything you want.

Then try opening the terminal again. It should create a new gnome-terminal folder, and if the error is within the original, terminal should now open.

mv oldname newname
right?
Its still not opening, tried it both on Unity and Gnome :-(
If it cant be fixed, is it ok to use Xterm, I mean is Xterm equivalent to the default Terminal?

---

### Post by drs305 on 2012-05-18
> **praveenkumarpon said:**
> mv oldname newname
right?


Here's what I had in mind, logged in normally (your username):
Original: ~/.gconf/apps/gnome-terminal
New:     ~/.gconf/apps/gnome-terminalx

Start gnome-terminal and if it starts, you should have it recreated as:
~/.gconf/apps/gnome-terminal

You could also try opening it via your working Xterm to see what, if any, error messages you get:
```
gnome-terminal
```

If you want to do it all in Xterm:
```

mv ~/.gconf/apps/gnome-terminal ~/.gconf/apps/gnome-terminalx
gnome-terminal
```

---

### Post by praveenkumarpon on 2012-05-18
ok, I got it.

Great, Now I get a message that there is no such file as "gnome-terminal" within ~/.gconf/apps
I only have these:
compiz-1   %gconf.xml   metacity   nm-applet   compizconfig-1   gedit-2   nautilus   panel

When I just open gnome-terminal through Xterm, I get this error:
Floating point exception (core dumped)

shall I just cat>gnome-terminalx within that folder? Sorry if I am wrong, I am new to all these :-)
nope, my idea did nothing ;-)

---

### Post by drs305 on 2012-05-19
I'd just rename gnome-terminalx back to gnome-terminal, then rerun the "gnome-terminal" command from Xterm and see if you get the same error. 

If you do, Google the exact message, and also include "gnome-terminal" and see what turns up.

---

### Post by drs305 on 2012-05-19
I'd just rename gnome-terminalx back to gnome-terminal, then rerun the "gnome-terminal" command from Xterm and see if you get the same error. 

If you do, Google the exact message, and also include "gnome-terminal" and see what turns up.

---

### Post by praveenkumarpon on 2012-05-21
solved it :P

I found it on:
[https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/990754]("https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/990754")

So, it seems changing fonts or even resetting it using UbuntuTweak renders the Terminal unusable.
Once if fonts are reset using MyUnity, Terminal is back again :lolflag:

What the hell is all these? Link between font settings and Terminal becoming unusable??

---

