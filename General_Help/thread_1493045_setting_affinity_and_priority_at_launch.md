---
title: "setting affinity and priority at launch"
date: 2010-05-25
forum: General Help
---

### Post by Hatuey on 2010-05-25
Hello all,

My problem: I have a molecular modeling program (MOPAC, but could be any other one) designed to work in serial (using only one CPU), and I want to launch a given number of MOPAC processes attached to different cores and with high priority.

Coming from Windows, this is as easy as: 

start /HIGH /AFFINITY 80 mopac2009 input_file.mop

where:

/HIGH: increase the process priority to HIGH
/AFFINITY 80: set the process to run only in CPU with hex code 80 (CPU 07 in an i7 Intel Processor)

The computer will be used only to do the calculation (i.e. no browsing, no messenger, no listen music, nothing!)

I had read about "taskset" and "nice", but I can not get both command working at the same time when launching the processes.

Any ideas/tips about implementing this in Linux?

Regards,

Hatuey

---

### Post by rg_stephens on 2010-05-26
You can start a process with the nice command. For a process that's already running, use the renice command. See ```
info renice
``` should give you more info. 

To start process at low priority:
nice -n 3 process

You have to be a superuser to start in high priority, or raise it: 
sudo nice -n -1 process

---

