---
title: "x11vnc question"
date: 2010-06-16
forum: General Help
---

### Post by miststlkr on 2010-06-16
I am running Mythbubntu 10.04 with two displays on separate X sessions and an x11vnc session on each, but i can only interact with the session which currently has the mouse on it at the server side.  Is there a way to change/fix this behavior?

---

### Post by krunge on 2010-06-17
> **miststlkr said:**
> I am running Mythbubntu 10.04 with two displays on separate X sessions and an x11vnc session on each, but i can only interact with the session which currently has the mouse on it at the server side.  Is there a way to change/fix this behavior?
Are these two separate X servers (i.e. DISPLAY :0 and DISPLAY :1) or two screens on one X server (i.e. DISPLAY :0.0 and DISPLAY :0.1) ?

Are there two separate monitors or are you switching sessions with one monitor? (e.g. Ctrl-Alt-F7 / Ctrl-Alt-F8 )

---

### Post by miststlkr on 2010-06-17
I have :0.0 and :0.1, each on different monitors.

---

### Post by krunge on 2010-06-17
> **miststlkr said:**
> I have :0.0 and :0.1, each on different monitors.
Running two x11vnc's one on :0.0 and another on :0.1 works properly for my system.

However I don't have a two monitor system with recent Xorg, so maybe Xorg broke something.

---

### Post by miststlkr on 2010-06-18
Guess I should have mentioned that; I am running XFCE 4.6.1 and x11vnc version 0.9.9

Perhaps the issue is in how I am working it?   I  have both vnc's running at login, one using ```
x11vnc -rfbport **** -many
``` and the other as 
```
 x11vnc -rfbport **** -many -display :0.1
```

Should I be using some command/argument to allow the mouse to work on both like I am trying or is it supposed to be working that way?

---

### Post by krunge on 2010-06-18
That should work.  That is basically what I did.  You might want to put "-display :0.0" in the first one to be explicit (but I am pretty sure that is the default).   I also assume you use something like 5900 and 5901 for the -rfbport's and then connect two viewers to these.

You can run the x11vnc's with "-dp" (-debug_pointer) to have it print out what it is trying to do with the pointer.  You will need to be able to view the output x11vnc prints out. Then you will at least see x11vnc is trying to inject the mouse input correctly.

I also suggest running a failsafe or twm session (but of course not gnome or kde) and verify that the problem still happens.  If it does, that will rule out the window manager.

---

### Post by miststlkr on 2010-06-19
Yes, both ports are in the 59xx range but thanks for checking.  I am/was prettyy sure that the -display :0.0 is implicit, but I'll give it a shot and see.  the failsafe/twm is new to me, I'll look into it.  Thanks.   I am also looking into using a ssh/putty/cigwyn combination but I do like the simplicity of a VNC setup over the LAN and as I understand it, the VNC *should* be able to do what I am trying to do.

Anyway, thanks for the pointers, I'll have a look at twm this weekend and see what that is all about.  Cheers!

---

### Post by krunge on 2010-06-19
You won't want to use the failsafe session or twm session for general usage; they are only for troubleshooting and diagnosing your problem.

Your login greeter (e.g. GDM) probably has 'failsafe' as an option, and maybe twm too once you add the twm package.

---

### Post by pfunk42 on 2011-03-30
I had this problem and with some looking around just discovered the -xwarppointer option to x11vnc, which fixes it.

---

### Post by krunge on 2011-11-19
> **pfunk42 said:**
> I had this problem and with some looking around just discovered the -xwarppointer option to x11vnc, which fixes it.

Yes, I finally found that this is a bug in Xorg with XTestFakeMotionEvent, more info here:

[INDENT][http://ubuntuforums.org/showthread.php?t=1858316](http://ubuntuforums.org/showthread.php?t=1858316)[/INDENT]

---

