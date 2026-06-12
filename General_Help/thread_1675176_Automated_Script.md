---
title: "Automated Script"
date: 2011-01-25
forum: General Help
---

### Post by Stefan_McFeeters on 2011-01-25
I am currently using Keryx to update my Ubuntu 10.10 system offline. I needed to create a script to install the packages downloaded from my computer connected to the Internet, then delete the packages after they  installed, then shutdown my computer. After the shutdown I then wanted my computer to reboot and run my File System Backup script. 

The script I created got as far as shutting down my computer after installing my downloaded packages, my problem is having my backup running immediately after I turn on my computer having run the package installer script (I do not want the backup running every time I turn on my computer, I only want it to run after I have run he package installer script)

Can anyone help menwith this problem.

---

### Post by sanderd17 on 2011-01-25
simple solution: let your package installer write a file, if the updater is run, he should first check if that file exists. If it exists, run the updater and delete the file.

> **Stefan_McFeeters said:**
> I am currently using Keryx to update my Ubuntu 10.10 system offline. I needed to create a script to install the packages downloaded from my computer connected to the Internet, then delete the packages after they  installed, then shutdown my computer. After the shutdown I then wanted my computer to reboot and run my File System Backup script. 

The script I created got as far as shutting down my computer after installing my downloaded packages, my problem is having my backup running immediately after I turn on my computer having run the package installer script (I do not want the backup running every time I turn on my computer, I only want it to run after I have run he package installer script)

Can anyone help menwith this problem.

---

### Post by Stefan_McFeeters on 2011-01-25
Sorry, but what you are saying does not make much sense. Where does the automated backup come into this (did I forget to mention that the backup is also run in terminal)

---

### Post by sanderd17 on 2011-01-25
sorry, 

let the PACKAGE INSTALLER write a file and the BACKUP should check if such a file exists.

Used the wrong names of the programs you run. Does it now make sense?

---

### Post by Stefan_McFeeters on 2011-01-25
As I said earlier, my main problem is running the backup immediately after I turn on my computer (but only when I have run the package installer script before the shutdown). I do not understand what you are telling me, sorry but can you make it anymore clearer.

---

### Post by sanderd17 on 2011-01-26
So currently you have the following:
[LIST]
[*]an update script (U) that you run manually
[*]a backup script (B) that you want to run when the computer boots but only if the update script has run before
[/LIST]

Is that correct?

I assume you know how to run a script after reboot, if you don't know that, google knows.

So what you do is: adapt the U script so that it writes a file at the end. e.g. you put the line 
```

$ date +"%y-%m-%d" > .script_has_run.file

```
at the end of your script.

Than you make a script like that: 

```

if [ `ls /home/user/.script_has_run.file` ]; then /home/user/backupscript.sh; fi
rm /home/user/.script_has_run.file

```

where "backupscript.sh is your B script. Make sure that the above script is executed at every reboot. So your B script will be executed if the U script ran before.

---

