---
title: "Cron job run with internet connection"
date: 2012-01-23
forum: General Help
---

### Post by gnome_nz on 2012-01-23
Hi all,

I've written a script that downloads a certain file for Windows machines and saves it under a filename based on the date - that works fine and is available to anyone else who wants it. 

I have also set a cron job to run this script on a weekly basis.

However, I cannot always guarantee that this machine will be on or connected to the internet at the time the job is set. What I need to know is how to make the job run at a time when the machine is on and has an internet connection, and if there isn't a connection (or the job is missed due to the machine being off) then to make it run at a later time, even the next day if necessary.

Any thoughts on how I'd do this?

Thanks in advance.

---

### Post by Paqman on 2012-01-23
> **gnome_nz said:**
> 
Any thoughts on how I'd do this?


Anacron.

Regular cron is designed for machines that are always on. For desktops you want to use anacron. Drop your script into /etc/cron.weekly and it'll be run once a week. Anacron is also significantly less faff to set up than cron. If your script is in the folder, it gets run. Simple as that, no config required.

As for the connection, just have the script ping google, or some other site you know will always be up, and exit if it fails.

---

### Post by gsgleason on 2012-01-23
Yes.  Ping something that works, and based upon the exit status, do your other stuff.

Put it all in a shell script, and have the cron job run the script.

```
#!/bin/bash
ping -c 1 -n 135.122.82.80 &> /dev/null
if [[ $? -eq 0 ]] #exit status 0 is success.
then
  #insert commands here
echo success
fi
```

---

