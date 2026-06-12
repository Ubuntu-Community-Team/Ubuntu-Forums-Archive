---
title: "Cron Jobs Not Running"
date: 2010-04-25
forum: General Help
---

### Post by jv2112 on 2010-04-25
My jobs wont run but they work fine if I manually run the scripts.

Any thoughts ?


Steps---->

Open Bash 
crontab -e
input
save

contrab -l output->

# m h  dom mon dow   command
30 7 * * * /joe/Scripts/BU
30 8 * * * /joe/Scripts/Clean

---

### Post by Zill on 2010-04-25
It seems to me that your path may be incorrect.  If the script you wish to run is in your home directory then you need to specify this eg...
```
~/joe/Scripts/BU
```

---

### Post by dcstar on 2010-04-25
> **Zill said:**
> It seems to me that your path may be incorrect.  If the script you wish to run is in your home directory then you need to specify this eg...
```
~/joe/Scripts/BU
```

No.

Never use anything but absolute paths in cron jobs.

Cron jobs are run in their own environment and there is no certainty that ANY shell commands or shortcuts that work in a terminal will work in cron.

As far as the OP goes, this may be correct:

```
/home/joe/Scripts/BU
```

---

### Post by Zill on 2010-04-25
> **dcstar said:**
> ...Never use anything but absolute paths in cron jobs...]
Agreed.  My error. :-?

---

### Post by jv2112 on 2010-04-25
THANK YOU !!!!!!!!!! :guitar:

---

### Post by geirha on 2010-04-25
```
~/Scripts/BU
``` is an absolute path though. Cron passes the command to /bin/sh, so the ~ will be expanded to the user's homedir.

Make sure to adjust the PATH variable appropriately in the script so that the shell will find all the commands.

[http://mywiki.wooledge.org/BashFAQ/072](http://mywiki.wooledge.org/BashFAQ/072)

---

### Post by dcstar on 2010-04-26
> **geirha said:**
> ```
~/Scripts/BU
``` is an absolute path though. Cron passes the command to /bin/sh, so the ~ will be expanded to the user's homedir.
........

Only on the **assumption** that everything is actually going to run in the particular shell environment that works in a terminal.

The whole point is that cron does not always run in that environment, and it is just good practice **never** to assume things like that and always use methods that take those assumptions out of the equation.

If you are going use those inside scripts called by a cron command then fine, just don't use them in the crontab file.

---

### Post by geirha on 2010-04-26
> **dcstar said:**
> Only on the **assumption** that everything is actually going to run in the particular shell environment that works in a terminal.

It's not an assumption if you read the docs. The expansion of tilde is defined by POSIX. 

> **dcstar said:**
> 
The whole point is that cron does not always run in that environment, and it is just good practice **never** to assume things like that and always use methods that take those assumptions out of the equation.


Cron's environment will be different from the one you have in a regular bash interactive shell, sure, but it is not random. Reading cron's documentation will tell you exactly what to expect; no need to assume anything.

---

