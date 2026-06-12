---
title: "Chose Recovery Console at shut down, how do get back?"
date: 2012-02-13
forum: General Help
---

### Post by Jgourd on 2012-02-13
Ubuntu 11.10 I was at the login prompt and chose "Recovery Console" .  It boots to a tiny terminal that won't take any keystrokes. If I hit Ctrl-Alt-F1 I can login and use the console. They made a way to switch into this thing, they must have made a way to switch back, right?

Please help.

---

### Post by efflandt on 2012-02-13
That tiny terminal was likely an xterm, but not sure why it was not taking keystrokes unless you have some video issues.  The way back to X from any console is Alt+F7 (Alt+F1 thru Alt+F6 are alternate consoles, or Ctrl+Alt+F1 thru Ctrl+Alt+F6 from X).

Or if all else fails and you are logged into a console, do: **sudo shutdown -h now** and start over.

---

### Post by Jgourd on 2012-02-13
When I do a shutdown it always comes back to the recovery console. I'll try the Alt-F7 thing.

---

### Post by Jgourd on 2012-02-14
Alt-F7 just brings me back to the command prompt that doesn't take keystrokes.

---

### Post by Jgourd on 2012-02-14
Isn't there a way to switch back? In Windows you hold F8 at boot and you can choose normal or recovery or safe mode. I manually chose this thing, what is the command to change what mode it boots to? startx fails because it thinks it is running. Unity --reset doesn't work. NOTHING I HAVE READ ABOUT OT TRIED WORKS.

Why is this hard? I clicked a little gear and chose recovery console. What is the command line equivalent that makes it so that Unity is the default GUI?

---

### Post by Jgourd on 2012-02-14
This turned out to be really simple but frustrating to solve.

It turns out the X Console I was logging into didn't have focus and that is why it did not take my keystrokes. I moved the mouse over the prompt and the keyboard worked. All I had to do was type "exit" and I was back to the GUI login screen. I changed the default interface back to Unity and all is good.

---

