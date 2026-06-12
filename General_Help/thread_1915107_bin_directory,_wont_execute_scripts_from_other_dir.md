---
title: "/bin directory, wont execute scripts from other directories"
date: 2012-01-25
forum: General Help
---

### Post by SoFl W on 2012-01-25
I created a ~bin directory and puts some bash scripts I created in there.

$PATH shows the bin directory exists, the scripts are executable.(755)  If I am in terminal the only place I can run the script is from the bin directory.  I can't run them from other directories.  If bin is in the path shouldn't the scripts be able to be run from anywhere?

---

### Post by Lars Noodén on 2012-01-25
There's a difference between ~bin and ~/bin 
I suspect you are trying for the latter.

---

### Post by SoFl W on 2012-01-25
No, I wanted the user bin directory, I thought it served the same purpose as the system bin but for the user only.

---

### Post by bab1 on 2012-01-25
> **SoFl W said:**
> I created a ~bin directory and puts some bash scripts I created in there.

$PATH shows the bin directory exists, the scripts are executable.(755)  If I am in terminal the only place I can run the script is from the bin directory.  I can't run them from other directories.  If bin is in the path shouldn't the scripts be able to be run from anywhere?

A bin directory in your $PATH should make available any executable file from anywhere.  Try ***strace*** to check and see what really happens.  I have an executable file in my bin directory called *cleanr*.  Here is the first line from this command *bab@mango:~$strace cleanr*```
$ strace cleanr
**[COLOR="Red"]execve("/home/bab/bin/cleanr"[/COLOR]**, ["cleanr"], [/* 37 vars */]) = 0

```

As you can see it has been executed.

---

### Post by SoFl W on 2012-01-25
Thank you for your help bab1, it helped me see what I was doing wrong.  "sh program-name.sh" does not work, "program-name.sh" works fine.  I kept trying to use the "sh" to call the program and that failed.

Thank you.

---

