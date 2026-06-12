---
title: "&quot;backend&quot; taking up 100% CPU"
date: 2010-04-30
forum: General Help
---

### Post by Queue29 on 2010-04-30
[IMG]http://i.imgur.com/dDkSV.png[/IMG]

What the heck is "backend" and why is it taking up 100% of one of my cores? I don't want to arbitrarily kill a root process w/o knowing what it is.

---

### Post by OlympicSoftworks on 2010-05-04
I have the same thing.  One of my procs is running with 'backend' at 100%.  The machine is still responsive and such, but I'm not really used to something like this.  A 'windows' environment, yet...but not GNU/Linux.

---

### Post by dino99 on 2010-05-04
i suppose you have sqlite installed as backend is part of sqlite (look into synaptic) but you can first kill the process.

---

### Post by bsell on 2010-05-04
Bug report here: [https://bugs.launchpad.net/checkbox/+bug/553328](https://bugs.launchpad.net/checkbox/+bug/553328)

It seems to happen after system testing.

---

### Post by frozenjim on 2010-05-05
Good observation.  Backend at 93% after running the system testing utility.  Reboot and it's back to normal.

---

### Post by Sepero on 2010-05-23
[https://bugs.launchpad.net/ubuntu/+source/checkbox/+bug/556636](https://bugs.launchpad.net/ubuntu/+source/checkbox/+bug/556636)

---

### Post by mkham on 2011-01-02
I have this problem- how come this hasn't been addressed in the Updates? My problem is more serious- I can stop or kill the backend, but the system seems to progressively clog up (even thought the processor isn't stressed), till the mouse freezes and have to do hard shut off. Restart still gives the same problem. 

I did use system test, but I also installed Thunderbird, and got it working directly off the mail stores in the Windows installation- I was terrified of messing up these stores but actually didn't think they were compatible with Ubuntu. Thunderbird also used sqlite. 

How do I fix this, and if I remove the Thunderbird, would it delete the mail stores. I am not a Linux programmer and can't see any installation instructions.

---

### Post by mkham on 2011-01-04
Actually it seems to be a problem w a debian AVG antivirus installation (use to scan Windows files), which was sucking 96% of processor power; then even with it half killed (the active scans- it opened about 5 instances of scan) where the pricessor was free, the memory and virtual memory were maxed out to the point of almost freezing the computer. When all its processes were stopped (10) the memory would free up.  Figured out how to update it- damn complicated, but can't seem to configure it to not try to do scheduled scan. Ready to uninstall it- probably just doesn't like AMD 64 version. 

Interestingly, I think maybe the backend processor pigout may have influenced the AVG to similar behavior. Though that's just a feeling.

---

### Post by Neva on 2011-02-22
Had this problem too in lucid 10.04. After running System / Administration / System Testing and exiting the program, the backend process would consume 100% CPU.

The workaround is to terminate the process manually. This can be done from the terminal:
1) run the command: **top**
2) observe the process ID (PID) number of the backend process
3) type q to exit top
4) run the command: **sudo kill -9 (BackendPID)**, for example sudo kill -9 16355

---

### Post by lliseil on 2011-11-12
Hi, had same issue on Joli OS 1.2 Live today after having launched runned then close the System report tool.
Thank you for the tip on this issue.

---

