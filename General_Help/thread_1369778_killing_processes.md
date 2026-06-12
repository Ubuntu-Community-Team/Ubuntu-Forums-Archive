---
title: "killing processes"
date: 2010-01-01
forum: General Help
---

### Post by TiuTalk on 2010-01-01
Hi there,

That's what i'm doing right now:

[LIST]
[*]On the startup I run this command
**gnome-terminal -x scriptname**
[*]When the script¹ open it's a eternal loop that keeps a process opened and re-open it when it crash or die
[/LIST]
At 06:00 everyday the process try to kill itself.. But the terminal window (opened by script¹) still open, so the script¹ don't detect that the process was killed/terminated..

If i try to **killall **or **pkill **the process, the gnome-terminal still open after the process was terminated.

How can I get rid of this? :/

All i need is:
1. Run the process when the computer goes on - OK
2. If the process crash or fail (closed), it's restarted - OK
3. At 06:00 the process is terminated/killed and re-opened - Not so good... I can "finish" the process, but the window still open

---

### Post by juancarlospaco on 2010-01-01
Kill the window :)

---

### Post by TiuTalk on 2010-01-01
Bah... How?! I have 2 or 3 terminal windows... Don't know how the select the right one

---

### Post by Barriehie on 2010-01-09
> **TiuTalk said:**
> Bah... How?! I have 2 or 3 terminal windows... Don't know how the select the right one

When the process' start have them echo their PID's to a file.  $$ is the PID in a bash script.

---

