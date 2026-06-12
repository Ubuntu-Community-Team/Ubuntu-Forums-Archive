---
title: "Ubuntu Freezes Every Few Days"
date: 2011-08-01
forum: General Help
---

### Post by goboni on 2011-08-01
Dear All,
We use Ubuntu 10.10 (32 bit) as a backup server.
The machine is quite ild but still working well.
All works very good but every few days it is crashed and freez.
I do not know what real happeny since i do not work on it, but tring to ping it fail and the monitor is blank.
 
What can I do?
Which log is relevant?
 
Best to all response

---

### Post by goboni on 2011-08-02
Any idea?
If I need to supply more detaile please let me know

---

### Post by goboni on 2011-08-02
Dear All,
We use Ubuntu 10.10 (32 bit) as a backup server.
The machine is quite ild but still working well.
All works very good but every few days it is crashed and freez.
I do not know what real happeny since i do not work on it, but tring to ping it fail and the monitor is blank.
 
What can I do?
Which log is relevant?
 
Best to all response

---

### Post by s.fox on 2011-08-02
Please do not create duplicate threads for your problem. Thank you.

Threads merged.

---

### Post by Erik1984 on 2011-08-02
> **goboni said:**
> Dear All,
We use Ubuntu 10.10 (32 bit) as a backup server.
The machine is quite ild but still working well.
All works very good but every few days it is crashed and freez.
I do not know what real happeny since i do not work on it, but tring to ping it fail and the monitor is blank.
 
What can I do?
Which log is relevant?
 
Best to all response

/var/log/kern.log I find useful. Also had some hangs lately (on 11.04 though), the log pointed me in the direction of the HD so it seems like a hardware related problem here. Whenever it hangs I get 'ata'-errors in the kern.log.

---

### Post by pieroxy on 2011-08-02
There's not much to go on over here. A couple of questions:

- A monitor attached to the VGA card of your server doesn't show anything?
- Are you running Ubuntu or Ubuntu - server? If Ubuntu can you provide us with the brand and model of your GC ? Unlikely to be the cause, but if your monitor displays nothing, there may be an issue with your GC
- Did you try running Memtest86+ ?

All in all, it looks like it could be a hardware issue.

---

