---
title: "REISUB or RSEIUB? Problems with freezing..."
date: 2010-10-18
forum: General Help
---

### Post by psyguy92 on 2010-10-18
Greetings :) I'm having freezing problems with 10.10, and holding Alt-SysRq + REISUB is able to do a soft reboot. 

1. Does the order matter? I've seen REISUB and RSEIUB. 
2. Any ideas what's wrong? Or what logfiles I could post?

Symptoms: 
Screen blanks (black)
Ctrl-Alt-F1 and Ctrl-Alt-Backspace don't work
Mouse freezes
Checked appearances to no effects, (preferences -> appearance -> no effects) thinking that might be the problem, but it froze again.

Was running chromium and transmission.

Thanks for any suggestions!

---

### Post by psyguy92 on 2010-10-23
Update: 

Installed xubuntu/xfce desktop and it seems to be doing well.
Also installed updates using update manager.
Will check Gnome again.

Anyone know if the order matters on REISUB / RSEIUB ?

---

### Post by spoon_ on 2010-10-23
Nvidia card by any chance? Anything in /var/log/Xorg.0.log (or /var/log/Xorg.0.log.old) along the lines of:

```
EQ overflowing. The server is probably stuck in an infinite loop.
```

---

### Post by psyguy92 on 2010-10-23
Looks like RADEON

Looking through: 
cat /var/log/Xorg.0.log
I see:

```

[  9129.045] (--) RADEON(0): Chipset: "ATI Radeon Mobility M6 LY (AGP)" (ChipID = 0x4c59)
[  9129.045] (II) RADEON(0): AGP card detected

```

Don't know how to 'grep' for "EQ overflowing", but it didn't seem to be there ? :/

---

### Post by spoon_ on 2010-10-23
Ok, you must have a different problem then. Your symptoms matched a problem I and some other Nvidia users had with Nvidia's PowerMizer technology and the latest Xorg server. Sorry, don't know what's causing your issues. It might be worth it to look for Xorg errors in that log file though, in case it's another Xorg issue.

---

### Post by ssulaco on 2010-10-23
> **psyguy92 said:**
> 
Anyone know if the order matters on REISUB / RSEIUB ?
No....
> unRaw      (take control of keyboard back from X),  
 tErminate (send SIGTERM to all processes, allowing them to terminate gracefully),
 kIll      (send SIGKILL to all processes, forcing them to terminate immediately), 
  Sync     (flush data to disk),
  Unmount  (remount all filesystems read-only),
reBoot.


---

### Post by KernelSpace on 2010-10-30
Its REISUB ie. BUSIER spelt backwards.

BTW welcome to the club, see here for more freeze related posts WARNING: 1000+ posts :-)
[http://ubuntuforums.org/showthread.php?p=10045433](http://ubuntuforums.org/showthread.php?p=10045433)

---

