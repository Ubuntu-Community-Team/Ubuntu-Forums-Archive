---
title: "unison does not work with cron"
date: 2011-11-29
forum: General Help
---

### Post by smee204 on 2011-11-29
Unison seems to run fine if run from the terminal so I have now added it to crontab. 
It runs as crontab and seems to work but cron reports it fails.

cron logfile:

Nov 29 20:45:01 simon-pc CRON[14873]: (simon) CMD (unison -batch lan_documents > /home/simon/unisondg.log 2>&1)
Nov 29 20:45:01 simon-pc CRON[14872]: (CRON) error (grandchild #14873 failed with exit status 1)

cron cmd:
* * * * * unison -batch lan_documents > /home/simon/unisondg.log 2>&1

the unisondg.log contains:
Contacting server...
Connected [//SERVER//mnt/data/simon_docs -> //simon-pc//home/simon/Documents]
Looking for changes
  Waiting for changes from server                                       
Reconciling changes
props    <-?-> props      /  
local        : dir props changed  modified on 2011-11-29 at 20:45:01  size 0         rwxr-xr-x
SERVER       : dir props changed  modified on 2011-11-29 at 20:44:38  size 0         rwxrwxrwx
No updates to propagate


Any ideas on what is wrong?

---

### Post by Habitual on 2011-11-29
Simon:

Try this:
```
vi ~/.unison/simon.prf
```
# Unison preferences file
### first root is the [COLOR="Red"]source[/COLOR] (from)
root = /home/jj
### second root is the [COLOR="Red"]destination[/COLOR] (to)
root = /media/Keepers

and run it manually with:
```
unison simon -batch -ui text -auto -silent
```
and stick that in a simon.sh file with 
```
#!/bin/bash
unison simon -batch -ui text -auto -silent
```
Save and exit simon.sh
Terminal > 
```
chmod 700 /path/to/simon.sh
```

Terminal > 
crontab -e (as user simon) and alter
```
* * * * * /path/to/simon.sh >/dev/null 2>&1
```

The default log file for unison is ~/unison.log so it is not clear to me why you are trying to use/force /home/simon/unisondg.log

Subscribed with interest...

HTH.

JJ

---

### Post by smee204 on 2011-11-30
Your example works and I managed to sync from a fresh empty folder on my pc to another fresh empty folder on my server. Just it does not work if I try and sync the folders I want to!

The thing that I don't get is that the cron says it fails with exit status 1 but it does actually sync the folders!

Strange...

---

### Post by Habitual on 2011-11-30
What is "lan_documents" exactly?

---

### Post by smee204 on 2011-12-01
lan_documents is one of my unison .prf files.

I managed to fix it by adding perms=0 in my unison profile file.
It turns out one file was skipped each run due to the permissions being different, just it was not displayed.

Thanks for the help!

---

### Post by Habitual on 2011-12-01
> **smee204 said:**
> ...i managed to fix it by adding perms=0 in my unison profile file...

+1

---

