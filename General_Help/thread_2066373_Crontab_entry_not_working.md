---
title: "Crontab entry not working"
date: 2012-10-04
forum: General Help
---

### Post by rmcellig on 2012-10-04
This is my crontab:

* * * * * rsync -r -n -t -p -g -v --delete -s /home/randy/Downloads/ /home/randy/Desktop/test # JOB_ID_1


When I use Grsync and press the Make a full run button it works but when the same code is in a crontab it doesn't. Nothing happens. What should I do?

---

### Post by lukeiamyourfather on 2012-10-04
Two things, if you run the command by itself in the terminal does it do what you expect? The other thing is you're telling the machine to run the command every minute. That's not a good idea. A more sensible command would be for once a day or maybe twice a day. Also restart the daemon when you make changes to the crontab.

---

### Post by cmont899 on 2012-10-04
always try yo use full paths in your crontab, your command switches can also be comined to look a bit cleaner

```
* * * * * /usr/bin/rsync -rntpgv --delete -s /home/randy/Downloads/ /home/randy/Desktop/test # JOB_ID_1
```

see if that helps at all

---

### Post by rmcellig on 2012-10-04
Thanks. All I want to do is test and see if my crontab works. Once it does, I will set up the approprite times for the crontab to work.So far no luck so what I would like to do is use the command line to set up a basic rsync. What could I do to test if just a basic simple rsync command works if that makes any sense.

---

### Post by ajgreeny on 2012-10-04
Use a  command like ```
/usr/bin/aplay /path/to/file.wav
```to test your crontab with any .wav file on your system.

It should be obvious as you will hear it when it plays, if it plays.  Full paths always should be used in cron as it will often not work if you use the normal terminal command for an application.

---

