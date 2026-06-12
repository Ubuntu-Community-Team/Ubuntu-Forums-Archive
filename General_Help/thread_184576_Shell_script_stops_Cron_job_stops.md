---
title: "Shell script stops/ Cron job stops"
date: 2006-05-30
forum: General Help
---

### Post by jonem on 2006-05-30
Good day fellow Ubuntu user,

I seems that my time consuming shell scripts for creating tar.gz files of all employees mail and document libraries stop after some time when executed by Crontab. I see the same behavior when I ssh in. If the link is broken the script is stopped soon after. This has not been the case when using other distributions such as Slackware or RedHat(Whiteboxlinux, Fedora).

Is this a antisipated behavior and is there a setting somewhere that I can change. Maybe a setting for orphan program instances or something similair?

Best Regards -Jon

---

### Post by Michal Fapso on 2006-06-06
Hi Jon,

there could be a limit for CPU time of each process. Try to run ```
ulimit -a
``` to see all limits. You can set unlimited CPU time with ```
ulimit -t unlimited
``` but the reason why your process is killed after some time might be also caused by exceeding some other limit like memory.

Good luck
Miso

---

