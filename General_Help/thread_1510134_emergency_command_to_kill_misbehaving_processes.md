---
title: "emergency command to kill misbehaving processes"
date: 2010-06-15
forum: General Help
---

### Post by jomex on 2010-06-15
I'm working with Eclipse and it's starting to misbehave now and then which completely freezes my computer. Is there any emergency command to kill such a misbehaving process so I don't have to reboot my computer?

I already have a emergency xkill icon in my taskbar and a [Ctrl]+[F1] console with "> sudo killall eclipse" pretyped(!) but sometimes it's even to late for this. What I would need is a emergency command/console that gets a guaranteed amount of process time so I can kill these process.

---

### Post by colorlessprism on 2010-06-15
In case of a freeze where you cannot do anything, simply press **_Alt+SysRq_+R+E+I+S+U+B**, the underlined keys must be kept pressed through the rest of the sequence AND that you will need to keep holding the sequence keys for a small period of time before going to the next one so that their actions can be carried out properly (For example, hold the R key for about 1-2 seconds before moving on to S). If it does not work at first, then increase the period between each key press and try again.

here is what is does:
**R**aw (take control of keyboard back from X), t**E**rminate (kill -15 programs, allowing them to terminate gracefully), k**I**ll (kill -9 unterminated programs),** S**ync (flush data to disk), **U**nmount (remount everything read-only), re**B**oot.

NOTE:- This keystroke does not work in the event of a kernel freeze as the keystroke sequence depends on the kernel in order to unmount and make the required steps before the restart.

---

### Post by jomex on 2010-06-15
very interesting, thank you, though [E] kills the whole X which is a bit extreme.

---

### Post by hariks0 on 2010-06-15
> **colorlessprism said:**
> In case of a freeze where you cannot do anything, simply press **_Alt+SysRq_+R+E+I+S+U+B**, the underlined keys must be kept pressed through the rest of the sequence AND that you will need to keep holding the sequence keys for a small period of time before going to the next one so that their actions can be carried out properly (For example, hold the R key for about 1-2 seconds before moving on to S). If it does not work at first, then increase the period between each key press and try again.

here is what is does:
**R**aw (take control of keyboard back from X), t**E**rminate (kill -15 programs, allowing them to terminate gracefully), k**I**ll (kill -9 unterminated programs),** S**ync (flush data to disk), **U**nmount (remount everything read-only), re**B**oot.

NOTE:- This keystroke does not work in the event of a kernel freeze as the keystroke sequence depends on the kernel in order to unmount and make the required steps before the restart.

Why such a long key press sequence is to be made? Can we assign some easy key strokes - Super Delete - to send the same command to kernel?

---

### Post by NYKevin on 2010-06-15
Have you tried switching tty's?  That can be done by pressing Ctrl+Alt+(F1-F6).  If it doesn't work, you need to use the SysRq sequence described above..  If it does, give it your username and password, then type
```
pgrep -l eclipse
```You should see output in the form of a number followed by the word "eclipse".  There may be other lines as well, but you can usually ignore those.  Type 
```
kill number
```where number is the number from the first command.
Repeat the first command (the pgrep one).  If you still see the "eclipse" line, do this:
```
kill -9 number
```If either of the kill commands give you permission errors, prefix them with sudo and try again (e.g. "sudo kill number").
Remember that you *need* to replace "number" with the actual number!
When you're done, press Ctrl+D and then Alt+F7 

(if Alt+F7 doesn't get you back to the desktop, first try Alt+F8, and if that doesn't work, do Alt+(F1-F6), log in, type the letter w and hit enter, then look for a line ending in "gnome-session" or something similar, find the tty column, and that row should have a tty value of ttyx where x is a number.  Press Ctrl+D and then press Alt+Fx, where x is that number)

Note that there's also a panel applet to "force a misbehaving application to quit", but that obviously won't work if the mouse won't move or something.

---

