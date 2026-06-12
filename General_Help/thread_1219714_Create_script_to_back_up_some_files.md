---
title: "Create script to back up some files"
date: 2009-07-22
forum: General Help
---

### Post by sim085 on 2009-07-22
Hi,

Being a new to linux, I do not know what or where to start searching about this!

Basically, following a tutorial, I managed to build a mail server. However this mail server is generating a lot of logs (also because of a minor problem I have).

What I want is to write a script that every month/week/day would:

1) Copy the files I want to back-up to some other location.
2) Empty the files containing the logs.
3) Delete any backups more then 6 months old.

Please do not mis-understand my about post. I am not asking for someone to 'do' me this. I am just asking for directions on where I could look for help (such as a tutorial).

There two problems I am facing - how to build the script, and how to make it run as part of some scheduler.

Regards,
Sim085

---

### Post by nothingspecial on 2009-07-22
See [here]("https://help.ubuntu.com/community/CronHowto")

and [here]("https://help.ubuntu.com/community/rsync")

---

