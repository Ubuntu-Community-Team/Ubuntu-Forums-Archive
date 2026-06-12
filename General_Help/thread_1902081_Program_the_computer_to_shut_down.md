---
title: "Program the computer to shut down"
date: 2011-12-29
forum: General Help
---

### Post by balampixan on 2011-12-29
Hello Ubuntu community!!!

Does any one of you know if there exists any software in ubuntu 64bit to program the computer to shut down at certain time?

Like if I want to shut down at 10pm for example... or 11:17pm etc...

Thank youuuuuu!!!!!
BalamP.

---

### Post by boast on 2011-12-29
if you're not looking for anything fancy, the shutdown command does it.

[http://linux.die.net/man/8/shutdown](http://linux.die.net/man/8/shutdown)

```
 Shutdown at 8 pm:
   shutdown -h 20:00

 Shutdown in 10 minutes: 
   shutdown -h +10 
```

---

### Post by yetiman64 on 2011-12-30
Look into either at or cron for shutting down at specific times (use "man at" or "man cron" in terminal for usage). Some examples,

for cron(tab), use ```
sudo crontab -e
``` and add the line,
```
17 23   * * *   shutdown -h now
```by putting the command in root's crontab there is no need for sudo in the command as any command in this crontab is executed as root (Take very careful note of this, and be careful what you launch from here). If the command does not need sudo (it does for shutdown though) consider using your user crontab with the command ```
crontab -e
```As has been noted previously, if you give shutdown a specific time to operate it will do so, but if the machine is restarted before the shutdown process previously set operates, the shutdown process itself will be killed off and will not operate as planned after the restart. cron and at both schedule the job so shutting down earlier or restarting will not affect them.

---

### Post by kostkon on 2011-12-30
> **balampixan said:**
> Hello Ubuntu community!!!

Does any one of you know if there exists any software in ubuntu 64bit to program the computer to shut down at certain time?

Like if I want to shut down at 10pm for example... or 11:17pm etc...

Thank youuuuuu!!!!!
BalamP.
Assuming that you are looking for an easy to use program, yes; [*gshutdown*]("https://apps.ubuntu.com/cat/applications/natty/gshutdown/"). Search for it and install it in software centre, or just press the *Install gshutdown* button on the above page.

Hope that helps.

EDIT: or maybe a better option would be [*qshutdown*]("https://apps.ubuntu.com/cat/applications/natty/qshutdown/"). Try this first.

---

### Post by balampixan on 2011-12-30
Thank you! That does the trick!

---

### Post by balampixan on 2011-12-30
Thank you! :)

---

### Post by balampixan on 2011-12-30
Thank you  :)

---

### Post by balampixan on 2011-12-30
Thank you :)

---

