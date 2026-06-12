---
title: "Crontab issue - program may not be running"
date: 2009-12-10
forum: General Help
---

### Post by lsutiger on 2009-12-10
I have a bash script setup in crontab. Here is the listing:
```
0 5 * * 0,2-6 copyfiles.sh >> COPY_ERR #JOB_ID_6
```

When I run the bash script on it's own, it works. When it is scheduled to run, nothing happens (no results). What the script does is copy files from one location to another on the network, both of which are owned by me. 

The script is supposed to run at 5 am, Sunday, and Tuesday through Saturday. 

The file COPY_ERR is created, but is empty.

Thank you in advance!

---

