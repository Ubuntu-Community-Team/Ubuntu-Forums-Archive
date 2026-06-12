---
title: "to find out program's computer resource usage"
date: 2010-05-17
forum: General Help
---

### Post by iochinome on 2010-05-17
Hello,

I am currently developing a program that i need to compare to other similar programs, mainly to provide a cost v. benefits analysis for myself and coworkers. does anyone know of a program that can accurately provide this information? or, otherwise, an idea of how to start coding?

I have seen in research papers before that quickness was actually evaluated in seconds/microseconds taken for processes to finish- is this legitimate??

thank you!

---

### Post by dv3500ea on 2010-05-17
Look up the 'time' command:
```

man time

```

---

### Post by dv3500ea on 2010-05-17
Look up the 'time' command:
```

man time

```

---

### Post by quadproc on 2010-05-17
> **iochinome said:**
> Hello,
...
I have seen in research papers before that quickness was actually evaluated in seconds/microseconds taken for processes to finish- is this legitimate??

thank you!
Yes, it is quite legitimate.  The answer from dv3500ea is an excellent place to start.

Some additional information: you can run the system monitor from the System > Administration collection and look at the Resources tab.  This shows a graphical display of the last minute's worth of processor activity, amongst other things.

The speed at which a computer runs is essentially that of the slowest thing in it.  That thing may be a peripheral, a DMA channel, memory bandwidth, or any of a lot of factors.  Offhand, the slowest thing that I can think of is a floppy disk.  The speed can vary from run to run depending on the nature of the tasks running on the system, the IO occurring, and the organization of the disk files being used.  Also, if your system has a small amount of physical RAM so that swap is being used then the speed will dramatically decrease.

quadproc

---

