---
title: "ushare daemon no longer starts automatically"
date: 2011-09-28
forum: General Help
---

### Post by gnomeout on 2011-09-28
I have been trying to fix this the last couple days. To be honest I cant even remember when it started.

But despite working with no issues for the last year, my ushare daemon process will not start on its own anymore. However once I am logged in, if I type ```
sudo service ushare restart
``` it will start up just fine (telling me it failed to kill ushare before restarting it).

Some googling shows some other people have the same problem, but I could not find a solution anywhere. 

I have tried looking for an output/log file somewhere but cant seem to find any. Which strikes me as completely ridiculous, so I must not be looking in the correct place. But nothing is coming immediately to mind for where to look.

If I check boot.log, it tells me it started ushare with no problems (status of "[OK]"). But I cant find any other log files relating to ushare, which is presumably where I will figure out why my daemon isnt starting...

Other things ive tried:
clean installation (had to manually wipe conf file, ubuntu would not do it even though I marked it for "complete removal")
Also tried 
```
sudo update-rc.d ushare defaults
```
and
```
sudo update-rc.d ushare enable
```

---

### Post by gnomeout on 2011-11-30
bump. I have now performed a clean installation of 11.10 and I am still having the same issue. This leads me to believe there is a configuration error somewhere that is being replicated across both installations.

Any ideas??? Anyone???

---

