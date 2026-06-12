---
title: "Cron setup"
date: 2010-07-13
forum: General Help
---

### Post by f1dreamer on 2010-07-13
Hi guys,

I want to add two separate tasks/jobs to Cron that needs to run every 10 minutes, but I would like the second job to kick off only 5 minutes after the first job. 

Is there any way this could be done within Cron?

Thanks,
Pieter

---

### Post by DaithiF on 2010-07-13
Hi,
no cron is not designed to do dependencies between jobs.

do they have to be separate cron jobs?  How about a single wrapper script which runs job1, sleeps for 5minutes, then runs job 2.  Then a single cron entry to call that wrapper script every 10mins.

---

### Post by f1dreamer on 2010-07-13
Hi DaithiF,

Thanks for the quick reply!  Thanks, that is a great idea!

Enjoy the week,
Pieter

---

