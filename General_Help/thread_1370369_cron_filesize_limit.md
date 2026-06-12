---
title: "cron filesize limit?"
date: 2010-01-02
forum: General Help
---

### Post by jkarpago on 2010-01-02
Hi:

I have a job that checks the files in a folder and then execute a ffmpeg command to transcode those videos. When I execute the command for myself it works perfect, but when the cronjob execs the script, the log files neccessary for the ffmpeg stops at 1mb file size. As I said if I exec the command manually it works perfect and the log files are about 6 mb.
I guess this is a limit in the filesize that cron can create, but I do not find anywhere.
Thanks for your help.

---

### Post by DaithiF on 2010-01-02
can you post the script / command?
thanks

---

