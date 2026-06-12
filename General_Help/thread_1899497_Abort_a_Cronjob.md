---
title: "Abort a Cronjob"
date: 2011-12-23
forum: General Help
---

### Post by drmota on 2011-12-23
Hello,

I have several cronjobs scheduled to run every hour. This means that the maximum time a cronjob is allowed to elapse is 1 hour. If the cronjob exceeds this limit, I need the cronjob to abort, rather than the other one starting and me ending up having two cronjobs running simultaneously.

Note that I don't want to delete the cronjob from the crontab. I just want to abort it if it exceeds a specified time limit. 

If you have external script, please give the source code :)

Thanks in advance,
Dr Mota

---

### Post by drmota on 2011-12-24
please reply :)

---

### Post by fdrake on 2011-12-24
> 
Note that I don't want to delete the cronjob from the crontab. I just want to abort it if it exceeds a specified time limit.

If you have external script, please give the source code

can you be more precise/descriptive on what you are trying to do?
you want the job to be canceled after running for a period of time or after the clock has reached a specific time?

also did you create a user cron job or a system(root) one?

---

### Post by Lars Noodén on 2011-12-24
You could do some kind of file locking.  I'm not sure if [flock](http://manpages.ubuntu.com/manpages/oneiric/en/man1/flock.1.html) is the way to go or not. A lot of services put the process id into a file in [font=Courier]/run[/font]

Your script could check for  the existence of a file in [font=Courier]/run[/font] and abort if the file exists.  When the script is finished running it should delete the file.

---

### Post by btindie on 2011-12-24
You can try with something like the following, put it at the top of your existing script and it'll kill any previous instances that are currently running.
```

#!/bin/bash

script=${0##*/}

for PID in $(pgrep $script); do
    if [ $PID -ne $$ ]; then
        echo "Killing existing instance with PID# $PID"
        kill $PID
    fi
done

trap "echo \"$script exiting.\"; exit 1" TERM

# Place your code here

SEC=0
while true; do
    sleep 1
    SEC=$((SEC+1))
    echo "I'm PID# $$, and I'm alive for $SEC seconds now!"
done

exit 0

```You can run the above script twice to see how it works.

Or you could use a wrapper script as described [here]("http://www.ibm.com/developerworks/library/l-job-terminating/index.html") to run it for a certain amount of time.

---

