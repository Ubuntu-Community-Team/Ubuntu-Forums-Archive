---
title: "Check hard disk"
date: 2010-02-27
forum: General Help
---

### Post by H.S. on 2010-02-27
Hi at all

I search for a Gui program that
running and check of the hard disk 
and monsters in graphical mode bad 
sectors. 

Thanks

---

### Post by -Robert- on 2010-02-27
I think GParted can do that job.
Boot from the LiveCD, start GParted (System > Administration > GParted), right-click on a partition and choose "Check".

Many HDD manufacturers provide their own diagnostic tools, you could also try that.
If you don't know the brand and type of your HDD you can copy/paste the following command in a terminal:

```
sudo lshw -html > hardware
```You can find the results in your home directory (look for a file called "hardware"), or just install [*hardinfo*]("https://help.ubuntu.com/community/HardInfo").

---

