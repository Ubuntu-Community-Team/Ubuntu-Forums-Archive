---
title: "what do you do when a application freezes?"
date: 2010-09-28
forum: General Help
---

### Post by warakawa on 2010-09-28
I downloaded this game called balazar from linux repository, and it just frozen when I tried to close it. Control+Alt+delete does not have end task option so what can I do to terminate the application in ubuntu?

thank.

---

### Post by claracc on 2010-09-28
You can open a terminal and write: ps -ef, there you look for the pid number of the process you want to end, then you write kill -9 pid number.

---

### Post by yetiman64 on 2010-09-28
Or you can "add to panel", the "force quit" applet. To use on a program click on the broken window icon and your cursor becomes a cross. Put the cross on the misbehaving application window and click it, then choose "Force Quit" or hit ESC on the keyboard if not needed.

---

### Post by dirghrabadia on 2010-09-28
> **yetiman64 said:**
> or you can "add to panel", the "force quit" applet. To use on a program click on the broken window icon and your cursor becomes a cross. Put the cross on the misbehaving application window and click it, then choose "force quit" or hit esc on the keyboard if not needed.

+1.

---

### Post by JoelOl75 on 2010-09-28
Unfortunately many games take over the whole screen, so the only way is ctrl-alt-F1 and 

killall balazar  

Or whatever it's called, like said, check with ps -A

---

### Post by warakawa on 2010-09-28
> **yetiman64 said:**
> Or you can "add to panel", the "force quit" applet. 

what and where is "add to panel"?? Sorry I am a beginner. 

Thanks.

---

### Post by sarin_cv on 2010-09-28
Press Alt + F2. Type xkill. This will also open the 'Force Quit' app.

---

### Post by jwbrase on 2010-09-28
You can also go to "System > Administration > System Monitor" and click on the "Processes" tab, find the misbehaving app, and kill it from there.

---

### Post by linux-hack on 2010-09-28
> **dirghrabadia said:**
> +1.

+2

---

### Post by yetiman64 on 2010-09-28
> **JoelOl75 said:**
> Unfortunately many games take over the whole screen, so the only way is ctrl-alt-F1 and 

killall balazar  

Or whatever it's called, like said, check with ps -A

This is good advice in that I hadn't considered full screen use (thus no panels etc).

Just note that with kill or killall the -9 option should be used as a last resort in case the app uses a lockfile and if poorly coded may not be able to clean up its own stale lockfile after a forced shutdown (may NOT be a problem with this game - though I'm not sure !) The TERM signal or -15 usually will do the job (-9 is intercepted at the kernel level not by the app as is -15 or others)

> what and where is "add to panel"?? Sorry I am a beginner. 

Thanks.      Just right click on any panel and it is the top option in the context sensitive menu.

---

### Post by warakawa on 2010-09-28
> **jwbrase said:**
> You can also go to "System > Administration > System Monitor" and click on the "Processes" tab, find the misbehaving app, and kill it from there.

Best advice so far, nice and easy for a windows user.  Thanks.

---

### Post by scouser73 on 2010-09-28
I go into System Monitor, find what's causing the problem and end the process.

---

