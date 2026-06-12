---
title: "Tabbed SSH"
date: 2009-10-20
forum: General Help
---

### Post by stevanbt on 2009-10-20
Hi,
I have seen this question asked before, but haven't seen a solution yet.

I'd like to know if it's possible to have a library of ssh sessions that will open in a new tab in a terminal window in Ubuntu.  

I use Putty Connection Manager in Windows which does roughly what I want, other than it's on Windows (Putty is in the repositories, but Connection Manager appears to be for Widnows only).

I have downloaded and installed SecPanel - that gives me a library of ssh connections, but when I open one of the connections it opens up a new terminal window.  Ideally I'd like it to open a new tab on an existing terminal window.

Failing that is there any way to do this in a shell script (setup a new ssh connection in an existing terminal window)?

In gnome-terminal I can see that it is possible to detatch a tab, but can't see that I can merge or add a tab.

Thanks, Steve.

---

### Post by regala on 2009-10-20
> **stevanbt said:**
> Hi,
I have seen this question asked before, but haven't seen a solution yet.

I'd like to know if it's possible to have a library of ssh sessions that will open in a new tab in a terminal window in Ubuntu.  

I use Putty Connection Manager in Windows which does roughly what I want, other than it's on Windows (Putty is in the repositories, but Connection Manager appears to be for Widnows only).

I have downloaded and installed SecPanel - that gives me a library of ssh connections, but when I open one of the connections it opens up a new terminal window.  Ideally I'd like it to open a new tab on an existing terminal window.

Failing that is there any way to do this in a shell script (setup a new ssh connection in an existing terminal window)?

In gnome-terminal I can see that it is possible to detatch a tab, but can't see that I can merge or add a tab.

Thanks, Steve.

I don't know about SecPanel but it should be in its configuration: you should be able to provide which commandline is used internally by the program to launch other gnome-terminals. If it's configurable, you have to set it to "gnome-terminal --tab" instead of "gnome-terminal --window" or even "gnome-terminal" by default.

hope this helps

br, mathieu

---

### Post by falconindy on 2009-10-20
You could always use the built-in, screen.

---

### Post by slakkie on 2009-10-20
> **falconindy said:**
> You could always use the built-in, screen.

it is not a built-in command, it is a separate program. If you run jaunty or later you can install byobu, which is screen + predefined screen profiles. Works really well. It it not really a tabbed ssh thing. But it has definite advantages. ssh to a single box once, start screen, have several "tabs" on that box. 

Btw, both Gnome terminal and Konsole (KDE terminal emulator) have tab support.

---

### Post by stevanbt on 2009-10-22
Hi,
Thanks for the replies.  I can't get 
```
gnome-terminal --tab 
```
to work.  I think it may be a bug [https://bugs.launchpad.net/gnome-terminal/+bug/117333]("https://bugs.launchpad.net/gnome-terminal/+bug/117333")??

I'll check out the other options asap.

Thanks, Steve.

---

### Post by kuthulu on 2010-04-08
try gcm, [http://kuthulu.com/gcm](http://kuthulu.com/gcm)

you can store your ssh/telnet sessions and open them in tabs

---

