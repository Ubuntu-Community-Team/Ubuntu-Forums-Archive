---
title: "&quot;shutdown&quot; in terminal vs &quot;shutdown&quot; in desktop"
date: 2010-02-26
forum: General Help
---

### Post by podge3 on 2010-02-26
This is driving me bonkers :mad:
 
I'm new to Ubuntu and have spent several days trying to make a few simple alterations to my Myth 9.10 installation.
 
My biggest task was to get the MCE "power" and "start" buttons working, which they now are - sort of.
 
The problem is with the shutdown command that the power button activates seems to be different to the shutdown command from the taskbar shutdown menu i.e. when I switch off the computer with the remote it restarts with the "recovery" menu as it wasn't shutdown properly. Same thing happens with the shutdown command from a terminal window. Shutting off from the desktop menu is fine. 
 
Does this make sense to anyone?

---

### Post by falconindy on 2010-02-26
/sbin/shutdown without extra parameters will actually do a restart. You need to specify the -h flag (for halt), or invoke 'halt' instead.

Also btw, if the package 'kexec' is installed, Ubuntu will use this when a reboot is requested. It's essentially a reboot but without going back to the BIOS. The "next" kernel is loaded into memory and takes over once the "current" kernel finishes execution. Keep in mind that the current and next kernel could be exactly the same one.

---

### Post by podge3 on 2010-02-27
Thanks for the reply, Falconindy.
 
Maybe I didn't explain myself properly - the PC does actually shutdown and switch off but when I next start it up I get the "recovery" screen with several options.

---

### Post by podge3 on 2010-02-28
Anyone?

---

### Post by rahilm on 2010-02-28
try "sudo poweroff" in the terminal

---

### Post by podge3 on 2010-02-28
> **rahilm said:**
> try "sudo poweroff" in the terminalAlready tried that - same problem when restarting.

---

### Post by Bronto on 2010-02-28
```
sudo shutdown -ah now
```

---

### Post by podge3 on 2010-03-01
> **Bronto said:**
> ```
sudo shutdown -ah now
```Just tried that - same problem unfortunately.

---

### Post by golanbatrac on 2010-03-01
This works for me:

```
sudo shutdown -P now
```

---

### Post by golanbatrac on 2010-03-01
> **Bronto said:**
> ```
sudo shutdown -ah now
```

What does the 'a' option do?  There's no 'a' option listed in the man page for 'shutdown'.

---

### Post by podge3 on 2010-03-01
> **golanbatrac said:**
> This works for me:
 
```
sudo shutdown -P now
```Just tried it - same problem.

---

### Post by Bronto on 2010-03-03
> **golanbatrac said:**
> What does the 'a' option do?  There's no 'a' option listed in the man page for 'shutdown'.

Yeah, sorry about that, old server habit. See this: [http://www.computerhope.com/unix/ushutdow.htm](http://www.computerhope.com/unix/ushutdow.htm)

---

