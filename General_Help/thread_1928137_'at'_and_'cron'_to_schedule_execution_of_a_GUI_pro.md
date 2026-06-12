---
title: "'at' and 'cron' to schedule execution of a GUI program"
date: 2012-02-19
forum: General Help
---

### Post by MGTHEBOSS on 2012-02-19
How to use 'at' and 'cron' to schedule execution of a GUI program?

I  scheduled opening gedit using 'at' but it didn't do anything.

See details please:

john@john-System-Product-Name:~$ at 23:55
warning: commands will be executed using /bin/sh
at> gedit
at> <EOT>
job 1 at Sun Feb 19 23:55:00 2012
john@john-System-Product-Name:~$ 

Thanks in advance to those who want to help.

---

### Post by Paddy Landau on 2012-02-19
To load a GUI program, you need to tell it where to display.

The command for gedit would be:
```
env DISPLAY=:0 gedit
```See the [community cron help]("https://help.ubuntu.com/community/CronHowto#GUI_Applications").

---

### Post by MGTHEBOSS on 2012-02-20
> **Paddy Landau said:**
> To load a GUI program, you need to tell it where to display.

The command for gedit would be:
```
env DISPLAY=:0 gedit
```See the [community cron help]("https://help.ubuntu.com/community/CronHowto#GUI_Applications").

Thanks. It worked.

---

