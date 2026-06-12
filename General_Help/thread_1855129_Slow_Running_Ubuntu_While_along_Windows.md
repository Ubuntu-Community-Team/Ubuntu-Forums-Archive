---
title: "Slow Running Ubuntu While along Windows"
date: 2011-10-05
forum: General Help
---

### Post by waltdog72080 on 2011-10-05
I have a Acer Aspire One running Windows 7 Starter and I decided to put Ubuntu along side it on the same hard drive. It ran nice for about a day or two, but then it started to run very slow.. I ran the "top" command and noticed that the CPU was running at 97.1%. Does anybody know what the problem is. Ubuntu is running so slow you can't do anything but hold the power button to turn the computer back off. Please help!!! Thank you in advance.

---

### Post by searchfgold6789 on 2011-10-05
You might check the filesystem for errors. ```
ckfs /dev/sda2
```from a live cd will do the trick (you may have to replace /dev/sda2 with a different device name). Also do a memtest.

---

### Post by Ranko Kohime on 2011-10-05
> **waltdog72080 said:**
> I ran the "top" command and noticed that the CPU was running at 97.1%.
Which process is using all that CPU time?

---

### Post by mikejonesey on 2011-10-05
whenever you get into a sticky situation u can usualy get away with switching to a terminal to sort the prob;
```
Ctrl+Atl+F1
```

to view your top cpu muchies;
```
ps -eo pcpu,pid,comm --sort pcpu | tail -5 | tac
```

at your own risk kill those processes...
```
ps -eo pcpu,pid,comm --sort pcpu | tail -5 | tac | cut -d " " -f 4 | xargs kill -9
```

but as ranko said... what is the command using the cpu?

---

### Post by waltdog72080 on 2011-10-22
Sorry for the late response, I have a Screen Shot attached to this post. I really don't see any programs taking all the CPU run time, I attached a copy of that too.

---

### Post by waltdog72080 on 2011-10-22
Okay, for some reason it looks as if I have AVG running a scan on the computer. I don't have AVG installed on the Ubuntu but it is installed on the same hard drive along side Windows 7. Do you think that has anything to do with it?

---

