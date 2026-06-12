---
title: "system locks for no apparent reason"
date: 2010-03-05
forum: General Help
---

### Post by prezbedard on 2010-03-05
Here are the symptons I launch firefox but it never opens. Its does have a process in system monitor but thats it. I kill it repeat and same thing happens. I attempt to open a terminal but all that opens is a blank gnome window that is titled terminal. The off/on panel button doesn't work. none of the panel buttons respond. I end up having to hit the reset or power button on the computer.

I have nothing else open at the time except pidgin and the weather widget.

This happens every so often but lately has been happening more. I do keep the system up to date.

any ideas on these anomalies? 

also is there anything like a "task manager" that can be launched with a keyboard combo when things lock up like this?

Thanks!

---

### Post by jerrrys on 2010-03-05
its called **system monitor** and you can find it in accessories...

---

### Post by prezbedard on 2010-03-07
> **jerrrys said:**
> its called **system monitor** and you can find it in accessories...

Yes I know. I use it often. The thing is when this happens I can't launch it.

---

### Post by rnerwein on 2010-03-07
hi
after login start in a terminal  top or htop with realtime priority.
chrt -r top
you must be super user to that.
may be this will help you because top or htop is then running in another scheduler queue.
ciao

---

### Post by prezbedard on 2010-03-07
ok I here is what i just did that repeated the issue. I opened firefox. It didn't launch. I went in to system monitor and it was sleeping. I killed it. I opened a terminal in launched a window titled terminal but was just a blank window. I opened system monitor and it was sleeping. I killed it. I hit the logoff/switch user/shutdown button and thats when nothing would respond. The only action that seem to respond to the mouse is right clicking the desktop.

not sure I get what you mean by the terminal top or htop. Are you saying to open a terminal then run 
"chrt -r top"? 

Thanks!

---

