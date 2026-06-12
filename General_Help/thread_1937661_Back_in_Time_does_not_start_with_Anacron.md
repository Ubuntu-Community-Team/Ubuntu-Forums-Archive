---
title: "Back in Time does not start with Anacron"
date: 2012-03-08
forum: General Help
---

### Post by Der Franz on 2012-03-08
Hi all,

I am quite unfamilar with Ubuntu, up to now I used Macs at home and Windows in the office. Now my mac is gone and I want to use Ubuntu. Making backups is a good idea, I decided to use Back in Time. The backup should start automatically. I tried a cronjob @reboot, but it did not work. A cronjob starting at a fixed time is not a good idea, because the computer is not up 24/7. So I would like to use Anacron. I have configured Back in Time (root) and placed a script in /etc/cron.daily. Target is an external USB hard disk.

The backup does not start, and I don't know why ...

This I find in the system log:

```
Mar  4 14:13:54 HP-Ubuntu anacron[1106]: Job `cron.daily' started
 Mar  4 14:13:54 HP-Ubuntu anacron[2253]: Updated timestamp for job `cron.daily' to 2012-03-04
 Mar  4 14:17:13 HP-Ubuntu kernel: [  518.522107] init: anacron main process (1106) killed by TERM signal
 Mar  4 16:43:27 HP-Ubuntu anacron[2862]: Anacron 2.3 started on 2012-03-04
 Mar  4 16:43:27 HP-Ubuntu anacron[2862]: Normal exit (0 jobs run)
 Mar  4 16:43:28 HP-Ubuntu anacron[3024]: Anacron 2.3 started on 2012-03-04
 Mar  4 16:43:28 HP-Ubuntu anacron[3024]: Normal exit (0 jobs run)
```This is the listing of /etc/daily.cron:
```
[FONT=monospace]
[/FONT]
franz@HP-Ubuntu:~$ ls -al /etc/cron.daily
 insgesamt 84
 drwxr-xr-x   2 root root  4096 2012-02-29 07:21 .
 drwxr-xr-x 147 root root 12288 2012-03-04 21:13 ..
 -rwxr-xr-x   1 root root   311 2010-06-20 10:11 0anacron
 -rwxr-xr-x   1 root root    95 2012-03-02 21:53 1backintime
```This is the script 1backintime:
```

#!/bin/bash
 export HOME=/root
 sudo -H "backintime -b > /dev/null 2>&1"
```And this is the anacrontab:
```

 # /etc/anacrontab: configuration file for anacron
 # See anacron(8) and anacrontab(5) for details.
 SHELL=/bin/sh
 PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
 # These replace cron's entries
 1       5       cron.daily       nice run-parts --report /etc/cron.daily
 7       10      cron.weekly      nice run-parts --report /etc/cron.weekly
 @monthly        15      cron.monthly nice run-parts --report /etc/cron.monthly
```The backup can be started manually in the Back in Time GUI, and with sudo backintime -b


I'll be happy about any advice ...

Best regards,

Franz

---

### Post by Dave_L on 2012-03-08
> sudo -H "backintime -b > /dev/null 2>&1"

I would redirect the output to a file, in case there's useful diagnostics.

For example:

```
sudo -H "backintime -b >> /var/backintime.log 2>&1"
```

---

### Post by Zill on 2012-03-08
Der Franz:  I don't use Back in Time so cannot confirm this but from the [Documentation]("http://backintime.le-web.org/documentation/settings-dialog/") it looks like you can schedule directly from the Setting Dialog GUI...
> Set where to save snapshots and schedule automatic backups: disabled, **at every boot**, every 5 minutes, every 10 minutes, every hour, every day, every week, every month.

---

### Post by Der Franz on 2012-03-08
Zill, yes, your are right. I tried it. "At ervery boot" is an entry in the crontab, @reboot. It did not work here.

Regards,

Franz

---

### Post by Der Franz on 2012-03-08
> **Dave_L said:**
> I would redirect the output to a file, in case there's useful diagnostics.

Dave, thank you for the reply. I copied the output from the terminal:

```
root@HP-Ubuntu:~# backintime -b

Back In Time
Version: 1.0.7

Back In Time comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to redistribute it
under certain conditions; type `backintime --license' for details.


(backintime.py:2316): Gtk-WARNING **: Im Modulpfad »pixmap« konnte keine Themen-Engine gefunden werden,

(backintime.py:2316): Gtk-WARNING **: Im Modulpfad »pixmap« konnte keine Themen-Engine gefunden werden,

(backintime.py:2316): Gtk-WARNING **: Im Modulpfad »pixmap« konnte keine Themen-Engine gefunden werden,

(backintime.py:2316): Gtk-WARNING **: Im Modulpfad »pixmap« konnte keine Themen-Engine gefunden werden,
INFO: Lock
INFO: [GnomePlugin.Systray.run]
 INFO: on process begins
INFO: [GnomePlugin.Systray.run] begin loop
INFO: Profile_id: 1
INFO: Compare with old snapshot: 20120304-210455-903
INFO: Command "rsync -rtDH --links -A -pEgo  --delete --delete-excluded  -i --dry-run --out-format="BACKINTIME: %i %n%L" --chmod=Du+wx  --exclude="... deleted..." / "/media/Backup HD/backintime/HP-Ubuntu/franz/1/20120304-210455-903/backup/"" returns 0
INFO: Create hard-links
INFO: Command "find "/media/Backup HD/backintime/HP-Ubuntu/franz/1/20120304-210455-903/backup/" -type d -exec chmod u+wx {} \;" returns 0
INFO: Command "cp -aRl "/media/Backup HD/backintime/HP-Ubuntu/franz/1/20120304-210455-903/backup/"* "/media/Backup HD/backintime/HP-Ubuntu/franz/1/new_snapshot/backup/"" returns 0
INFO: Command "find "/media/Backup HD/backintime/HP-Ubuntu/franz/1/20120304-210455-903/backup/" -type d -exec chmod a-w {} \;" returns 0
INFO: Command "chmod -R a+w "/media/Backup HD/backintime/HP-Ubuntu/franz/1/new_snapshot"" returns 0
INFO: Call rsync to take the snapshot
INFO: Command "rsync -rtDH --links -A -pEgo  --delete --delete-excluded  -v  --chmod=Du+wx  --exclude="... deleted..." / "/media/Backup HD/backintime/HP-Ubuntu/franz/1/new_snapshot/backup/" 2>&1" returns 0
INFO: Save config file
cp: angegebenes Ziel „HD/backintime/HP-Ubuntu/franz/1/new_snapshot/backup/..“ ist kein Verzeichnis
WARNING: Command "cp /root/.config/backintime/config /media/Backup HD/backintime/HP-Ubuntu/franz/1/new_snapshot/backup/.." returns 256
INFO: Save permissions
INFO: Create info file
INFO: Command "chmod -R a-w "/media/Backup HD/backintime/HP-Ubuntu/franz/1/20120305-183919-486/backup"" returns 0
INFO: Command "chmod -R a-w "/media/Backup HD/backintime/HP-Ubuntu/franz/1/20120304-210455-903/backup/"" returns 0
INFO: Remove backups older than: 20020305-000000
INFO: Keep min free disk space: 1024 Mb
INFO: [GnomePlugin.Systray.run] end loop
INFO: Unlock
root@HP-Ubuntu:~# 
```I deleted the --exclude options for better readability.

Regards,

Franz

---

### Post by Erik1984 on 2012-03-08
Looking at that logfile this seems to go wrong (commands that exit with status 0 are good):

```

cp: angegebenes Ziel &#8222;HD/backintime/HP-Ubuntu/franz/1/new_snapshot/backup/..&#8220; ist kein Verzeichnis 
WARNING: Command "cp /root/.config/backintime/config /media/Backup HD/backintime/HP-Ubuntu/franz/1/new_snapshot/backup/.." returns 256

```

It's the space in the volume name "Backup HD" that is causing the problem as it seems.

---

### Post by aeiah on 2012-03-08
if all you want to do is run it every boot then just put it in your /etc/rc.local before the exit 0. it'll run as root.

```

backintime -b &

exit 0 
```

or you could use the GUI to set a schedule rule so it only backs up once a day, and then use this command in rc.local or even cron:
```

backintime --backup-job
```

according to the manual:> –backup-job – take a snapshot (if needed) depending on schedule rules (used for cron jobs).



i set my backup to run 15 minutes after boot. to do that in rc.local (and only have it run if it hasn't done so already today - or whatever you set your schedule rules to):
```

(sleep 15m && backintime --backup-job)&

```

---

### Post by Der Franz on 2012-03-08
> **Euroman said:**
> ]It's the space in the volume name "Backup HD" that is causing the problem as it seems.

Euroman, thanks for the reply. No, it isn't. I renamed the hard disk to Backup_HD, still no automatic backup. But the output of backintime -b changed to (copied just the snippet with the error) :

```
INFO: Save config file
INFO: Command "cp /root/.config/backintime/config /media/Backup_HD/backintime/HP-Ubuntu/franz/1/new_snapshot/backup/.." returns 0
INFO: Save permissions

```Just to remember: The manual backup works, just the automatic backup with anacron fails.

Best regards,

Franz

---

### Post by Der Franz on 2012-03-08
aeiah, thanks for your reply. No, it does not seem to work. I tried your first suggestion (backintime -b & in /etc/rc.local). Back in Time should start after a reboot - it doesn't. The rc.local is executable:

```
franz@HP-Ubuntu:~$ ls -al /etc | grep rc.local
-rwxr-xr-x   1 root root      323 2012-03-08 20:32 rc.local
```
I took a look at the /etc/init.d/rc.local according to [https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/882254](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/882254), and I changed the line ```
if [ -x /etc/rc.local ]; then
``` to ```
if [ -e /etc/rc.local ]; then
```No result. I changed it back now.

Best regards,

Peter

---

### Post by Der Franz on 2012-03-10
I can start rc.local via terminal, but no automatic start.

Now I added backintime -b to the Startup Applications. Back in Time runs now at every startup. Obviously, only a workaround, because one snapshot every day is enough. Each snapshot takes about 1.5 up to 2 hours.

Regards,

Franz

---

### Post by Der Franz on 2012-03-11
Now it's running with anacron: The script named 1backintime in /etc/cron.daily is now:

```
#!/bin/bash export HOME=/root backintime -b > /dev/null 2>&1
```According to [https://answers.launchpad.net/backintime/+question/150089](https://answers.launchpad.net/backintime/+question/150089) this should work only for Back in Time < Version 1.0.
I am using Version 1.0.7 ...

Best regards,

Franz

---

