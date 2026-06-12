---
title: "CPU 100% - Phantom usage"
date: 2012-05-24
forum: General Help
---

### Post by steve7777777 on 2012-05-24
I'm running 10.10. CPU is Phenom 955 with 8GB of memory.

CPU has was hot - 60c so checked CPU usage and two of four CPU's were 100%! Vino-server was using high % of resources so killed that and now after reboot one CPU still 100%, and temp is 51c - not ideal but ok for now. After reboot, CPU low across the board, and temps is 42c.

After reboot the CPU usage creeps up on a single CPU up to 100%, and system monitor -> Processes -> % CPU shows only gnome-system-monitor using 16%, nothing else being used.

I looked for this problem and there was a bug - phantom CPU usage but you'd think this was solved by now? Any ideas?

Thanks!

**[COLOR=Red]Update: turns out running TOP in terminal showed that apt-get was using 100%.I should have tried this first. [/COLOR]**

---

### Post by mister_playboy on 2012-05-25
Sounds like you are dealing with a zombie process... I agree that it can be very irritating the system monitor programs often do not show these.

The most common culprits for zombie on my system have been Java programs and the console.  You usually need to stop the parent process to get rid of the problem.

> A process can be sleeping in kernel code. Usually that's because of faulty hardware or a badly written driver- or maybe a little of both. A device that isn't set to the interrupt the driver thinks it is can cause this, for example- the driver is waiting for something its never going to get. The process doesn't ignore your signal- it just never gets it.
A zombie process doesn't react to signals because it's not really a process at all- it's just what's left over after it died. What's supposed to happen is that its parent process was to issue a "wait()" to collect the information about its exit. If the parent doesn't (programming error or just bad programming), you get a zombie. The zombie will go away if its parent dies- it will be "adopted" by init which will do the wait()- so if you see one hanging about, check its parent; if it is init, it will be gone soon, if not the only recourse is to kill the parent..which you may or may not want to do.
* Finally, a process that is being traced (by a debugger, for example) won't react to the KILL either.

We can find out zombie process by :-
Use top or ps command:

# top
OR
# ps aux | awk '{ print $8 " " $2 }' | grep -w Z
#ps -el | grep Z

How do I kill zombie process?
You cannot kill zombies, as they are already dead. But if you have too many zombies then kill parent process or restart service.

You can kill zombie process using PID obtained from any one of the above command. For example kill zombie proces having PID 4104:
# kill -9 4104
*Please note that kill -9 does not guarantee to kill a zombie process

Taken from a blog turned up by Google search... Blogger flags the blog as possibly containing adult content (???) so I'm not linking to it here.

---

### Post by steve7777777 on 2012-05-25
> **mister_playboy said:**
> Sounds like you are dealing with a zombie process... I agree that it can be very irritating the system monitor programs often do not show these.

The most common culprits for zombie on my system have been Java programs and the console.  You usually need to stop the parent process to get rid of the problem.



Taken from a blog turned up by Google search... Blogger flags the blog as possibly containing adult content (???) so I'm not linking to it here.

Thanks, I'll give it a try later tonight. 

I found this:
[http://www.debian-administration.org/articles/261](http://www.debian-administration.org/articles/261)

[FONT="Courier New"]With a normal ps -el command you see an output with in the second colum the state of the process. Here are some states:

S : sleeping
R : running
D : waiting (over het algemeen voor IO)
T : gestopt (suspended) of getrasseerd
Z : zombie (defunct)[/FONT]

---

### Post by steve7777777 on 2012-05-25
I ran this in terminal:
ps -el | grep 'Z'


```
steve@htpc64:~$ ps -el | grep 'Z'
F S   UID   PID  PPID  C PRI  NI ADDR SZ WCHAN  TTY          TIME CMD
5 [COLOR="Red"]Z[/COLOR]     0  2186  2184  0  80   0 -     0 exit   ?        00:00:00 [COLOR="red"]chromium-browse[/COLOR] <defunct>
steve@htpc64:~$
```


So Chromium Browser is causing the problem? But one CPU is at 100% after reboot without opening Chromium.

[http://code.google.com/p/chromium/issues/detail?id=92004](http://code.google.com/p/chromium/issues/detail?id=92004)

---

### Post by mister_playboy on 2012-05-25
I forgot about Chromium zombies... I have seen that before myself.

100% CPU from a fresh boot implies one of the startup process is to blame.  Does system monitor show anything?  Any zombie processes found then?

On KDE I occasionally get 100% CPU when the file manager (Dolphin) gets "stuck" trying to display file previews. Do you have your file manager start up at login?

---

### Post by steve7777777 on 2012-05-25
removed

---

### Post by steve7777777 on 2012-05-26
I rant TOP in terminal, and apt-get was at 100%

     ```
sudo killall apt-get                                 
```

And CPU usage is normal.

Under System->Startup Applications 
unticked "check for new hardware drivers" and "update notifier"

As mentioned I'm running an unsupported version - 10.10 but I hope this can help someone else. I should have started out by running TOP in terminal.

---

### Post by steve7777777 on 2012-05-26
removed

---

### Post by CharlesA on 2012-05-26
Did it do the same after a reboot?

---

### Post by steve7777777 on 2012-05-26
> **CharlesA said:**
> Did it do the same after a reboot?

After several reboots still no problem. CPU usage is low.
Again, the only thing I did was kill the apt-get and make the changes to Startup Applications.

---

### Post by CharlesA on 2012-05-26
> **steve7777777 said:**
> After several reboots still no problem. CPU usage is low.
Again, the only thing I did was kill the apt-get and make the changes to Startup Applications.
Even tho 10.10 is EOL, it shouldn't be using that much CPU.

I suppose that is a partial fix.

---

### Post by steve7777777 on 2012-05-27
I found the identical problem discussed [http://www.linuxquestions.org/questions/ubuntu...]("http://www.linuxquestions.org/questions/ubuntu-63/apt-get-always-running-in-background-866924/")

tried:

```
sudo apt-get clean
```

Still came back. Still not solved.

---

### Post by Handssolow on 2012-05-31
Just chipping in to report something similar but it may not be connected. I'm on 11.10 32bit pae Gnome Classic 4gb with AMD Phenom x6 core CPU. 

For about the past 4 days after I first noticed the fans were working faster than normal but assumed it was the hot weather then found one of the 6 cores of the CPU was 100%. Closing Firefox nothing much showed up in "Processes". A reboot temporally stopped this behaviour but after a few minutes one of the cores would go up to 100%. I've had the core go down to 0% then another core would shoot up to 100%. This continued for the last few days, such that I was unwilling to leave the PC unattended.

Hoping it wasn't a hardware fault, I was looking at a fresh install (probably of 64bit this time). Then today there are kernel updates which seems to have cured the problem and so far it hasn't reappeared.
uname -r shows 3.0.0-21-generic-pae

I assume it was a bug but my searches so far haven't found anything relevant.

---

