---
title: "Changing the priority of process"
date: 2012-02-26
forum: General Help
---

### Post by emptycoder on 2012-02-26
I'm having some problems with GNOME 3 Shell, it works fine with the latest ATI Driver 12.1 but so far I'm having two problems, The performance is slow and sometimes the shell flashes and disappears then returns back in few seconds, but sometimes it disappears and suddenly falls back to classic mode without panel and all I can do is pressing alt+ctrl+del to logout and then login back again.
So I thought that I might get a better profromnce if I could give GNOME-Shell the highest priority, but I couldn't change the priority on the System Monitor, an error messeage says: Can't change priority's process with pid 2841 to -5. Access denied
Then I thought of run it as a root with this command:
```
gksu gnome-system-monitor
```But when I do that, I can't fine gnome-shell on the processes list.
Could anyone help me out here? Thanks!

---

### Post by SeijiSensei on 2012-02-26
Use the Terminal and run **renice**.  Type "man nice" and "man renice" at the prompt for details.  To change the priority of a process you do not own, use "sudo renice".

You can also change priorities from **top**.  Open a terminal and run "sudo top".  Typing "r" will give you the option to change a priority by process ID.

---

### Post by emptycoder on 2012-02-26
After typing r then choosing ID, I got this:
Renice PID 5518 to value: 
What's the value for highest priority?
And what if I want to set it back to default?
 Sorry but I'm still a noob!

---

### Post by sudodus on 2012-02-26
from ```
man renice
``` you can read
```
     For example,

     renice +1 987 -u daemon root -p 32

     would change the priority of process ID's 987 and 32, and all processes
     owned by users daemon and root.

     Users other than the super-user may only alter the priority of processes
     they own, and can only monotonically increase their ``nice value'' within
     the range 0 to PRIO_MAX (20).  (This prevents overriding administrative
     fiats.)  The super-user may alter the priority of any process and set the
     priority to any value in the range PRIO_MIN (-20) to PRIO_MAX.  Useful
     priorities are: 20 (the affected processes will run only when nothing
     else in the system wants to), 0 (the ``base'' scheduling priority), any&#8208;
     thing negative (to make things go very fast).

``` So ***-20 < nice-value < 20*** but use 19 instead of 20.

*Edit: -20 gives your process highest priority, but I do not recommend that, because important system processes may suffer. Instead give background jobs (e.g.backup) high positive values. Maybe you can use -10 for a user process.*

---

### Post by emptycoder on 2012-02-26
Many Thanks!

---

### Post by SeijiSensei on 2012-02-26
For something I really want to priortize I'll use -15.

---

### Post by emptycoder on 2012-02-27
I'm facing a new problem, the gnome-shell's PID always changes, it's not the same PID numbers, so I have to change the priority every time I start up my system, how I can fix that?

---

### Post by SeijiSensei on 2012-02-27
You probably need to rewrite the command that executes when the shell is launched to use something like

```
nice -n -10 /path/to/gnome-shell
```

but since I don't use GNOME, I can't tell you where that would happen.

---

### Post by emptycoder on 2012-02-27
I tried that command and I got this:

```
user@ubuntu:~$ sudo nice -n -15 /usr/share/gnome-shell
[sudo] password for user: *********
nice: /usr/share/gnome-shell: Permission denied

```I don't know what's going on, I thought that I would gain full access as a root, but getting permission denied was odd.
Any idea?

---

