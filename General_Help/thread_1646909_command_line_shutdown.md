---
title: "command line shutdown?"
date: 2010-12-16
forum: General Help
---

### Post by hardyn on 2010-12-16
previously i could shut a machine down from the command line:

sudo shutdown now

with maverick this seem to crash the system?  similar symptoms on two machines, my desktop and notebook.

the desktop brings up a blue curses recovery screen, the notebook seems to just park at a black screen with some errors.

machines shuts down fine from the gui, what changed?

---

### Post by dabl on 2010-12-16
Try it with the -h option:

```
sudo shutdown now -h
```

---

### Post by Tralce on 2010-12-16
or

```
sudo poweroff
```

sudo reboot is also handy.

---

### Post by spydeyrch on 2010-12-16
> **dabl said:**
> Try it with the -h option:

```
sudo shutdown now -h
```

@dabl,

what is the '-h' argument/option in the end? Just curious. :) I am not at a machine that has a linux terminal so I can't use the 'man' command right now. Sorry. Thanks for the help.

-Spydey

---

### Post by Tralce on 2010-12-16
```
  -h     Requests  that  the system be either halted or powered off after
              it has been brought down, with the choice as to which left up to
              the system.

```

---

### Post by spydeyrch on 2010-12-16
Perfect. Thanks for the quick info. :)

-Spydey

---

### Post by bouncingwilf on 2010-12-16
Thanks for that - I always used sudo shutdown -g0 -i0  - That's all I could remember from my Unix days (works fine with Linux though)

Bouncinwilf

---

### Post by karthick87 on 2010-12-16
For poweroff,
```
shutdown -h now
```

For restart,
```
shutdown -r now
```

---

### Post by amauk on 2010-12-16
-h halts the machine*
-P powers off the machine
-r reboots the machine

*Halting a machine can mean different things (often configurable in the BIOS)
Normally for desktop machines, the BIOS powers off the machine when asked to "halt"

An interesting tit-bit, you mentioned the system "crashing" when you shutdown. Well, that's exactly what happens behind the scenes.
The OS puts itself into a clean state, then issues a command to the CPU that stops all system operations.
Halting a system is a controlled crash

---

