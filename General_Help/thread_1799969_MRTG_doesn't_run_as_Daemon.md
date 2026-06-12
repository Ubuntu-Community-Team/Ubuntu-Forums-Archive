---
title: "MRTG doesn't run as Daemon"
date: 2011-07-08
forum: General Help
---

### Post by wooju86 on 2011-07-08
Hello,

I set up MRTG on my ubuntu 10.10 using this link:

[http://www.iceflatline.com/2009/08/how-to-install-and-configure-mrtg-on-ubuntu-server/](http://www.iceflatline.com/2009/08/how-to-install-and-configure-mrtg-on-ubuntu-server/)

Now, i am trying to set it up so it refreshes every 5 minutes... I tried program scheduled task be entering /etc/init.d/mrtg start but it does not work... I also added the RunAsDaemon: Yes line to mrtg.cfg file but still nothing. 

It works fine from the terminal but not from the program... any ideas? 

Thanks in advance. 
Peter

---

### Post by SeijiSensei on 2011-07-08
I haven't run MRTG for a long time now, but as I recall, you needed to run it from cron.  I think you need to add a line to /etc/crontab that looks something like this:

```
*/5 * * * * root /path/to/mrtg /path/to/mrtg.cfg >> /var/log/mrtg_errors 2>&1
```

---

### Post by wooju86 on 2011-07-08
Thanks SeijiSensei, would you mind providing the code i need to use and where to do do it? Is the crontab the actual file i need add the lines to? 

I am sorry but i am complete Linux rookie...

---

### Post by SeijiSensei on 2011-07-08
Use "sudo nano /etc/crontab" to edit the file.  Add the command to the bottom of the file.

Using [this guide]("http://oss.oetiker.ch/mrtg/doc/mrtg-unix-guide.en.html"), jump down to Configuration and follow the steps outlined.

I assume you know the directory locations of the mrtg binary and mrtg.cfg.  Pay particular attention to the example for "like this if you use /etc/crontab".

---

### Post by wooju86 on 2011-07-08
I've added the line to the crontab and i can see it in the "Sheduled task". i will check it it works and let you know.

---

### Post by wooju86 on 2011-07-08
So, it doesn't work... I'll try to provide some more information. Content of crontab: 

```
*/5 * * * * root /etc/init.d/mrtg /etc/mrtg/mrtg.cfg
```

When i execute that in "Scheduled task" it comes up with error that i need to start/restart etc. So the actual script which i can execute is:

```
*/5 * * * * root /etc/init.d/mrtg start /etc/mrtg/mrtg.cfg
```

But is still does not work automatically... Does it matter that i am on the client not server version?

---

### Post by SeijiSensei on 2011-07-08
[QUOTE=wooju86;11026784]So, it doesn't work... I'll try to provide some more information. Content of crontab: 

```
*/5 * * * * root /etc/init.d/mrtg /etc/mrtg/mrtg.cfg
```

Items in /etc/init.d are startup scripts intended to start daemons at boot.  Somewhere there is a binary called mrtg, probably /usr/bin/mrtg or maybe /usr/sbin/mrtg.  That's what you need in the first part of the command.

Try running "sudo /usr/bin/mrtg /etc/mrtg/mrtg.cfg" from a command prompt.  What happen?

---

