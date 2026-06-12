---
title: "Fullscreen application hangs, what do you do?"
date: 2011-04-06
forum: General Help
---

### Post by sandle on 2011-04-06
**Hi!**
I have tried to search for similar stuff but havent found anything.

I'm using Ubuntu 10.10 x86_64 with Gnome, ATI hd3430 (ya I know ATI...).

The problem is that fullscreen applications hangs all the time for me and when they do, I can't do anything.

**The typical case for me:**
Trying to run something, application hangs.
The screen is either black or an image of the previous used app (aka not responding).

This is when i try all sorts of key-combinations to get out of it to either get to a console or some other way to shut the crashed application down, but since the application is crashed and all the keys are overrided (either that or not responding), I cant do anything.

**Things I've tried pressing:**
*ctrl+alt+delete* (you never know if something useful will happend (: )
*ctrl+alt+f1* (I actually thought this would work, but no)
*alt+tab* (this was my second hope!)
*alt+f4*
*esc* (a classic)
*every-button-on-my-keyboard-preferably-simultaneously* (nope, still doesnt do it)

**So my question is, what can i do when a fullscreen application crashes?**

The thing I've been doing is holding the power button ony my laptop, but I think its totally unnecessary (if not annoying) to restart the whole system just because of an app crashing (I mean it is linux I'm running here, stuff crashes all the time).

Sorry for my bad english, I'm somewhat writing this post in rage for restarting my laptop 15 times the last 10 minutes.

Greetings, sandle.

---

### Post by sandle on 2011-04-06
I have been thinking of binding something like xkill to a keypress for situations like this, although I have no idea on how to make a keypress that can be pressed even if a fullscreen application is running and has crashed.
([Binding Xkill]("http://ubuntuforums.org/showthread.php?t=531971"))

Searched around abit and it seems like ctrl+alt+f1 should be working?
It sure does'nt work for me.

---

### Post by Topsiho on 2011-04-06
I miss one possibility you did not mention: ctrl+alt+backspace, for logging out.

But my hope is very small this will work, if ctrl+alt+f1 (or f2 or f3 etc also don't work (to give you a terminal in which you can reboot or halt, or do top to see what process is using all the resources).

I sympathize with your frustration :(

Topsiho

---

### Post by sandle on 2011-04-06
Oh I forgot to mention, I have tried that also. It does'not work.

Well if I had a terminal I could enter commmands in it would'nt be a problem. I would like to know if there is any way to either get a terminal or to close the app, I am currently going to try using the xkill binding.

---

### Post by nothingspecial on 2011-04-06
Alt-SysRq at the same time the (with them held) R I E S U B (one after another).

---

### Post by WorMzy on 2011-04-06
You could use the magic SysRq key sequence to force a graceful restart. You need to enable this on Ubuntu before you can use it, so add ```
kernel.sysrq = 1
``` to /etc/sysctl.conf to enable it at boot time.

Once it's enabled, you can use it by pressing and holding Alt+SysRq, then pressing K. That should kill all processes running in the current virtual terminal, including X (which should then respawn). It's a little heavy handed, but if you can't access a TTY to kill the offending process, this is the next best thing.

Another key combination to remember is Alt+SysRq+R+E+I+S+U+B, as mentioned by nothingspecial. Here's what each letter does:

```
un**R**aw      (take control of keyboard back from X),  
 t**E**rminate (send SIGTERM to all processes, allowing them to terminate gracefully),
 k**I**ll      (send SIGKILL to all processes, forcing them to terminate immediately), 
  **S**ync     (flush data to disk),
  **U**nmount  (remount all filesystems read-only),
re**B**oot.
```

You should leave a slight pause between each letter, to give the command time to execute.

---

