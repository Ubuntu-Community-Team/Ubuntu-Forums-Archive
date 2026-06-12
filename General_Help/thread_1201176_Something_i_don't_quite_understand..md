---
title: "Something i don't quite understand."
date: 2009-06-30
forum: General Help
---

### Post by ethoxyethaan on 2009-06-30
Hello reader, I have a question about the following situation:

I have a perl script placed in the directory /usr/bin/, full path = /usr/bin/script10

to envoke it in shell i type:

```
Nick@ubuntu:~$ script10
```

to envoke it from python i use:

```
>>> import os
>>> os.system(script10)
```

My intend was to run a python script every minute in cron that countains the lines:

```
import os
os.system(script10)
```

this script worked perfectly from my terminal session, and ran without errors using cron, except for 1 thing, it did not execute "script10", after hours of debugging the script finding for other things that could have caused it to malfunction i came to the conclusion that i need to use the FULL path of the executable...

my question is WHY do these things work normally in terminal sessions (where you can read the output nicely) and won't work when you use them with cron (making it harder to tell where it went wrong...)

can someone give me the full history on this, because i feel i'm missing out on something here.

---

### Post by blueridgedog on 2009-06-30
When you are running a script, you have a path variable, you can see it with:

```
echo $PATH
```

Root has no path (as a safety feature) and things run at the system level (such as the system crontab) have no path.  With no path they only look in the current working directory for the referenced item.  When developing scripts and other items for system maintenance or operation, you should use a full path.

---

### Post by t4thfavor on 2009-06-30
so a crontab of 
1-59 * * * * /usr/bin/python script.py

then inside of script.py 
import os
os.system(/usr/bin/script10)

that should work.

probably dumb, but is that all the py script does? If so you should concider ditching it altogether, and just run the script10

---

### Post by ethoxyethaan on 2009-07-02
No this is not all the python script does, thanks blueridgedog.

---

