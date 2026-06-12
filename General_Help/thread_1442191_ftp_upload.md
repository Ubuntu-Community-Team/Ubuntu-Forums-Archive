---
title: "ftp upload"
date: 2010-03-29
forum: General Help
---

### Post by CatchItBaby on 2010-03-29
i want to upload some files to my server at a particular time how to do ?

or 

I want to upload some files from my pc to server at scheduled time ?

Thanks

---

### Post by geirha on 2010-03-29
For running a script or command at scheduled times, one typically uses cron. [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

For a one time job, you can use *at*. [http://manpages.ubuntu.com/manpages/karmic/en/man1/at.1.html](http://manpages.ubuntu.com/manpages/karmic/en/man1/at.1.html)

---

### Post by CatchItBaby on 2010-03-31
i want to open exe file through wine in ubuntu at a particular time how to do ?

edit : i did

50 10 * * * /home/username/Desktop/mysoftware.exe 

but didn't work

---

### Post by geirha on 2010-03-31
.exe-files are not executable in linux. You need to run wine and pass the exe file as argument.

```
wine "$HOME/Desktop/mysoftware.exe"
```

However, for X11 applications, cron is not the best tool. Install [gnome-schedule](apt:gnome-schedule), then go to Applications -> System tools -> Scheduled tasks and add it there.

---

