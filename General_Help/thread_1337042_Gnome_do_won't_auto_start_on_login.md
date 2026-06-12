---
title: "Gnome do won't auto start on login"
date: 2009-11-25
forum: General Help
---

### Post by humphreybc on 2009-11-25
Hey for some reason Gnome Do won't auto start when I login, even though it has that option checked under its preferences, and an item listed under "Startup Applications."

Interestingly, Gnome Do will launch if I manually click it from the menu, and it runs fine after then.

When it's running, I have two processes for it. (see screenshot).

What could the problem be? Mono not starting correctly at session start?

---

### Post by Mr. Devil on 2009-11-25
Haven't used it but delaying the launch should solve the problem.

gnomedo-launch.sh
```
sleep 30
gnome-do &
```

Add it to the list of startup applications ( remove the original Gnome Do entry ) and restart your PC.

---

### Post by humphreybc on 2009-11-25
Nope doesn't seem to work. I made the script and set it as executable, and played around with the delay value but no cigar.

It doesn't appear to be launching a process even.

---

### Post by leveliv on 2009-11-25
you also could have just added it to Startup Applications. even though its already in there you can make a new one. maybe use a different command to open it.

---

### Post by ninjapirate89 on 2009-11-25
This may be a stupid suggestion but are you sure you are pushing the right key combination to pull it up? Win+Space by default I believe.

---

### Post by stinkeye on 2009-11-25
_[COLOR="Red"]EDIT:[/COLOR]_If your using compiz and fusion-icon try this first.
In startup applications change the command to start fusion-icon to
```
fusion-icon -n
```
Which will run fusion-icon but stop it from loading a window manager.
I used to have a problem at startup where compiz would load by default but then fusion-icon would reload compiz causing gnome-do to crash.

If that doesn't work....

If your using compiz try this solution that worked for another user.
[_[COLOR="DarkRed"]http://ubuntuforums.org/showthread.php?t=1328943[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=1328943")

or for the launch script try```
sleep 30 [COLOR="DarkRed"]&&[/COLOR]
gnome-do &
```

---

### Post by humphreybc on 2009-11-25
> **ninjapirate89 said:**
> This may be a stupid suggestion but are you sure you are pushing the right key combination to pull it up? Win+Space by default I believe.

No i'm using the Dock for Gnome Do, so it should just appear down the bottom of my screen.

[QUOTE=leveliv]you also could have just added it to Startup Applications. even though its already in there you can make a new one. maybe use a different command to open it.[/QUOTE]

I've already tried this, doesn't work.

---

### Post by humphreybc on 2009-11-25
**EDIT: Okay no scratch that, it only worked when I logged out and back in, but not when I restart. **

Well I added the extra && to my script and used the -n command at the end of the compiz fusion icon startup entry.

I've managed to get it working with only a delay of 5 seconds. Cheers guys!

---

