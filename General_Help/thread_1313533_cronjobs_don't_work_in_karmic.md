---
title: "cronjobs don't work in karmic??"
date: 2009-11-03
forum: General Help
---

### Post by van_Zeller on 2009-11-03
Hello all,

I use my laptop as my alarm clock, for waking up with music. For some time (and some versions of ubuntu) I have followed this tutorial:
[http://ubuntuforums.org/showthread.php?t=185993](http://ubuntuforums.org/showthread.php?t=185993)
and it has worked fine.
However, for some reason on this latest (Karmic) release it no longer works. Here is my crontab:

```
0 8 * * 1 export DISPLAY=:0 && vlc --random /media/documents/documents/Musica/Tudo/ # JOB_ID_1
0 10 * * 2 export DISPLAY=:0 && vlc --random /media/documents/documents/Musica/Tudo/ # JOB_ID_2
```

If I copy and paste the command above, it works on the console. So what am I doing wrong?

Please help, its very frustrating coming back to the alarm clock!!

Thanks

---

### Post by van_Zeller on 2009-11-09
Sorry to bump this, but I really need my alarm clock back!

---

### Post by falconindy on 2009-11-09
Put the commands into a script file and add the script file to the crontab. Don't forget to make the script executable.

---

### Post by van_Zeller on 2009-11-10
Can you help me do this? I don't know how to...

---

### Post by diskmaster23 on 2009-11-10
[http://ubuntuforums.org/showthread.php?t=572194](http://ubuntuforums.org/showthread.php?t=572194)

This might help.

Just swap out your command for your script.

Ask more questions if you cannot figure this out.

---

