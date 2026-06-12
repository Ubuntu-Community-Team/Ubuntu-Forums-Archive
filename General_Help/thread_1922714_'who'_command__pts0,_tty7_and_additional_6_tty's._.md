---
title: "'who' command:  pts/0, tty7 and additional 6 tty's. Why?"
date: 2012-02-09
forum: General Help
---

### Post by Hadeda on 2012-02-09
In other posts, it was explained why the 'who' command shows pts/0 and tty7. I am running live CD (USB stick) and noticed an additional 6 tty's (tty1 through to 7).  
System monitor (resources) lists 6 (not 7, as expected) 'bash' processes in a n_tty_sleep state.

Is this normal and what is this about?

---

### Post by raja.genupula on 2012-02-09
[http://www.basicconfig.com/linux/linux-who-command-tutorial](http://www.basicconfig.com/linux/linux-who-command-tutorial)

that link have everything . 
 hope that helps.

---

### Post by Khayyam on 2012-02-09
Hadeda ..

It's normal. The tty's are spawned by at boot by 'getty' (normally six are spawned), the seventh, tty7 is normally reserved for X11 (your "login" screen and X11 session).

If you look in /etc/inittab you will see:

```
1:2345:respawn:/sbin/getty 38400 tty1
2:23:respawn:/sbin/getty 38400 tty2
3:23:respawn:/sbin/getty 38400 tty3
4:23:respawn:/sbin/getty 38400 tty4
5:23:respawn:/sbin/getty 38400 tty5
6:23:respawn:/sbin/getty 38400 tty6
```This is the default, but tty's can be added or reduced in number.

'getty' is just a small daemon that'll spawn a the tty for 'login', if login exits it'll respawn the tty so another person can login. It's much like a doorman opening and closing a door when people enter or exit a building.

On a (non-X11) tty you will see a 'login' prompt, this is the result of 'getty' and 'login'. On an X11 tty you will see a login manager (such as xdm, gdm), when you logout getty respawns the login manager.

HTH ...

---

### Post by Hadeda on 2012-02-09
I am glad that it is normal.

Raja - Yours is an excellent link which might answer many other questions I  have.

Khayyam - I like your doorman analogy. 

I am a bit edgy when it comes to 'users' as I have reasons to assume that the machine in question was in "the custody and control" of someone else during a drill at a seminar. I have problems ever since and am not an expert but a user.

What is a X11 tty ? In a single user system do I have/need something like that?
Thanks!

---

### Post by Khayyam on 2012-02-09
> **Hadeda said:**
> What is a X11 tty? In a single user system do I have/need something like that?

Hadeda ..

X11 is the abreviated name for the [X Window System]("http://en.wikipedia.org/wiki/X_Window_System"), and a 'tty' is the name given to a 'terminal', its name is derived from the historical [teletypewriter]("http://en.wikipedia.org/wiki/Teleprinter") or teleprinter.

X11 is the underlying foundation of your GUI, it provides the capacity to 'draw' elements to your screen, render fonts, etc. On Linux, X11 is provided by the [Xorg Foundation]("http://www.x.org/wiki/"). Its not "neccessary" but if you want a GUI then you need X11 and a 'tty' for it to 'draw' on. As I illusrtated previously a tty can present you with 'login' (a non-graphical user interface to login to the system) or a (graphical) 'login manager' (such as gdm, kdm or xdm). When you are presented a 'screen' this is a tty, the terminology is slighty different from the way 'screen' or 'display' is commonly used (ie: 'monitors' are called 'displays') as the *nix analogy developed when there were no graphical displays and all 'output' was printed to a teletype printer. A tty is not limited to your actual visual display (monitor) there can be many tty's running on one machine, just as there can be many printers (teleprinters). You currently have seven tty's you could use, currently your viewing tty7, the other 'displays' are hidden from you but you can swich to them by hitting control-alt-F1 to F7 (tty7). When you switch tty you will see 'login' running on tty1, tty2, tty3 ..., and on tty7, X11 (which is rendering Unity Desktop, Gnome, KDE, or what-have-you). The idea is that whatever is currently providing the display is just an interface, and can be pushed aside for another interface, this means that two or more X11 sessions, an emulator, etc, etc, etc, can run simultaniously, and you can switch between them (again, very different from what people are use to ... with MacOS or Windows for instance, they are presented with the GUI as **the** interface).

So, it's not a matter of you "needing it or not" (you could remove the tty's spawned by getty from /etc/inittab .. but there is no real reason do so), its part of the design, *nix is after all a multi-user, and multi-task system. It is the advantages provided by that design that make much of what Linux is able to do possible. Even on a "single user" machine there good reasons for having more than one single input-output.

HTH ..

---

### Post by Hadeda on 2012-02-10
Thank you all.

Khayyam:

> very different from what people are used to ... with MacOS or Windows.

Your concise and newbie language can achieve a change in mindset from Windows to Ubuntu.
It is now easier for me to understand more involved issues.

You have done a great job and your efforts are much appreciated!=D>

---

### Post by Khayyam on 2012-02-11
> **Hadeda said:**
> Khayyam [...] Your concise and newbie language can achieve a change in mindset from Windows to Ubuntu. It is now easier for me to understand more involved issues.

Good ... I'm pleased you understood. Not to keep on about it, but you'll encounter this input/output ('stdin' and 'stdout' ... or [standard streams](http://en.wikipedia.org/wiki/Standard_input)) model (and the reasons for keeping it abstracted from, and not locked to, the keyboard, display, controller, process, etc) the more you gain experience with *nix. You'll see that it becomes alot easier to 'chain' things together, to have one process provide input for another (etc, etc), because of this design.

> **Hadeda said:**
> You have done a great job and your efforts are much appreciated!

Your welcome .. best khay

---

### Post by savanna on 2012-02-11
These are spawned by getty. Getty comes from the "olden days" when people had dumb serial monitors that would connect to "mainframes" via serial lines.

You can still do this sort of thing eg setup one powerful Linux machine, and connect multiple dumb terminals to it. Handy when you've got lots of people doing one simple task that only needs to run one or two simple programs eg in call centres, banks.

---

### Post by Hadeda on 2012-02-13
> Handy when you've got lots of people doing one simple task

I will keep that in mind, savanna.

Once again, thanks to you all!

---

### Post by Khayyam on 2012-02-13
> **savanna said:**
> [...] Getty comes from the "olden days" when people had dumb serial monitors that would connect to "mainframes" via serial lines.

Actualy it predates monitors, it was developed to handle [teletype printers](http://en.wikipedia.org/wiki/Teletype) .. see [getty's wikipedia page](http://en.wikipedia.org/wiki/Getty_%28Unix%29).

More useless information .. but maybe interesting

best ... khay

---

