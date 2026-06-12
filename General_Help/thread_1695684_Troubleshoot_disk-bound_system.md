---
title: "Troubleshoot disk-bound system?"
date: 2011-02-26
forum: General Help
---

### Post by perstromgren on 2011-02-26
Cheers!

What tools are for troubleshooting a system, that seems to be diskbound? 

My computer is sluggish, although there are plenty of unused CPU and memory (according to the System Monitor), and very low network traffic is displayed. 

An ideal solution would be some program that tells me what process is generating the most I/O:s and perhaps also the ratio of elapsed time that the system is waiting for I/O. 

Is there such a program out there?

Per.

---

### Post by wt8008 on 2011-02-26
I recommend installing iotop
```
sudo aptitude install iotop
```
It is a console program that lists processes by IO usage.

Let me know if it works!

---

### Post by perstromgren on 2011-02-27
Thanks, wt8008, that is the tool, of course! Now on the harder part, analysing... 

It seems that the browser itself is doing a lot of I/O, which blocks it. I also see a lot of activity in the jbd2 process. I must now try to see what comes out of this.

Per.

PS.Is it possible to enable CONFIG_TASK_DELAY_ACCT in a ready-built kernel? DS

---

