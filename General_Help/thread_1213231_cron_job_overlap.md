---
title: "cron job overlap"
date: 2009-07-14
forum: General Help
---

### Post by abazoskib on 2009-07-14
i have a cronjob set up with crontab -e as

```
01 * * * * /path_to_my_script &
```

It is a .PHP script.

I am not gaurenteed that the script will finish in an hour time. How can I make sure crontab only runs the next scheduled time for this script if it is not currently running?

---

### Post by abazoskib on 2009-07-14
well in case anyone stumbles across this i got a solution.

create a temporary file(lock file/blank file) that the script checks for on start..if the file exists exit the script..if it doesnt exist, create the file and proceed.

---

