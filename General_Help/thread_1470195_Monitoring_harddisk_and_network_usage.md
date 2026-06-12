---
title: "Monitoring harddisk and network usage ??"
date: 2010-05-02
forum: General Help
---

### Post by xx77aBs on 2010-05-02
Hello ! Is there any program (something like top or htop) that would give me a list of processes that are using harddisk in percentage or something, so that I can see what process is using the hard disk the most ??

Also, is there the same thing, but for network interface ? (I want to see top programs that are transferring data over eth0)

It doesn't need to be program, it can be shell script or just give me something to work with, I don't know where should I start :)


Thanks !!

---

### Post by spiky001 on 2010-05-02
system administration system monitor

---

### Post by xx77aBs on 2010-05-02
sorry, I forgot to mention, I need something that will work over SSH ;)

---

### Post by spiky001 on 2010-05-02
I take it you have tried using top over ssh?

---

### Post by xx77aBs on 2010-05-02
yes top and htop, but I can only use them for CPU and memory usage :)

I can't see how much network bandwidth is process using or if it's writing on HDD (and how much ...)


I think that I can't see that things in system monitor too

---

### Post by spiky001 on 2010-05-02
how about iftop?
[http://www.google.co.uk/#hl=en&source=hp&q=check+for+bandwidth+usage+ubuntu&meta=&aq=f&aqi=&aql=&oq=&gs_rfai=&fp=22911715a928b061](http://www.google.co.uk/#hl=en&source=hp&q=check+for+bandwidth+usage+ubuntu&meta=&aq=f&aqi=&aql=&oq=&gs_rfai=&fp=22911715a928b061)

---

### Post by xx77aBs on 2010-05-03
yeah, that's it, thanks !! Is there any way to see name of the process ??

And is there anything like that for harddisk ?

---

### Post by cryptotheslow on 2010-05-03
For the harddisk use iotop :)

---

### Post by xx77aBs on 2010-05-07
hm I get this error:


- Linux >= 2.6.20 with I/O accounting support (CONFIG_TASKSTATS, CONFIG_TASK_DELAY_ACCT, CONFIG_TASK_IO_ACCOUNTING): Not found


does that mean that I need to recompile kernel ?

---

