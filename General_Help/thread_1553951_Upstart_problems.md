---
title: "Upstart problems"
date: 2010-08-15
forum: General Help
---

### Post by russellr on 2010-08-15
Hi,

Ubuntu Lucid (10.04)

I've been working for *many* hours trying to get a job to start on boot.

It has some dependencies, but when I couldn't get that to work, I went for a simple test case:
```

description     "Test Service"

start on startup
respawn

script
    echo "***** `date`" >>/var/log/rr.log
    exec sleep 60
end script

```

That doesn't work! :confused:

I've started the kernel with --verbose and --debug and the relevant lines in /var/log/syslog are:
> 
Aug 16 12:02:32 machine init: job_class_register: Registered job /com/ubuntu/Upstart/jobs/test


Nothing else!

Replacing the "start" line with this:
```

start on runlevel [2345]

```

does work. And here are the lines from syslog:
> 
Aug 16 12:05:07 machine init: job_class_register: Registered job /com/ubuntu/Upstart/jobs/test
Aug 16 12:05:07 machine init: job_class_register: Registered job /com/ubuntu/Upstart/jobs/smstest
Aug 16 12:05:08 machine init: job_class_register: Registered job /com/ubuntu/Upstart/jobs/test
Aug 16 12:05:08 machine init: job_class_register: Registered job /com/ubuntu/Upstart/jobs/smstest
Aug 16 12:05:10 machine init: job_class_register: Registered job /com/ubuntu/Upstart/jobs/test
Aug 16 12:05:10 machine init: job_class_register: Registered job /com/ubuntu/Upstart/jobs/smstest
Aug 16 12:05:10 machine init: job_register: Registered instance /com/ubuntu/Upstart/jobs/test/_
Aug 16 12:05:10 machine init: job_register: Registered instance /com/ubuntu/Upstart/jobs/test/_
Aug 16 12:05:10 machine init: event_pending_handle_jobs: New instance test
Aug 16 12:05:10 machine init: test goal changed from stop to start
Aug 16 12:05:10 machine init: test state changed from waiting to starting
Aug 16 12:05:10 machine init: test state changed from starting to pre-start
Aug 16 12:05:10 machine init: test state changed from pre-start to spawned
Aug 16 12:05:10 machine init: test main process (526)
Aug 16 12:05:10 machine init: test state changed from spawned to post-start
Aug 16 12:05:10 machine init: test state changed from post-start to running
Aug 16 12:05:12 machine init: job_class_register: Registered job /com/ubuntu/Upstart/jobs/test
...



Why doesn't this basic upstart stanza (start on startup) work?

Am I missing something?

regards,
RR

---

### Post by sisco311 on 2010-08-16
> **russellr said:**
> 

Why doesn't this basic upstart stanza (start on startup) work?



Probably because Upstart runs the job before the filesystems are mounted. 

Try something like:
```
start on filesystems
```

---

