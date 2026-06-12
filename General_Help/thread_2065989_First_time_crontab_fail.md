---
title: "First time crontab fail"
date: 2012-10-03
forum: General Help
---

### Post by GRX13 on 2012-10-03
> # Output of the crontab jobs (including errors) is sent through
# email to the user the crontab file belongs to (unless redirected).
#
# For example, you can run a backup of all your user accounts
# at 5 a.m every week with:
# 0 5 * * 1 tar -zcf /var/backups/home.tgz /home/
#
# For more information see the manual pages of crontab(5) and cron(8)
#
# m h  dom mon dow   command
@reboot qbittorrent
@reboot ~/Documents/rtorrent_cron

Nothing happens on turning the machine on. Running the second command script by itself beginning from '~' works and so does typing 'qbittorrent' into terminal. Crontab tells me it installs the cronjobs after saving in nano after running crontab -e.

Why does qbittorrent not start or my script runs on powering on/reboot?

---

### Post by usalug on 2012-10-03
Check permissions of the files.  Pehaps they are set to user only and not user group. Also, putting in the FULL PATH of the script/program your trying to run is always a good thing. cron doesn't always have the same PATHs by default that you might think it does.

---

### Post by GRX13 on 2012-10-03
chmod 777 on the script so full permissions. Changed the path on QB to /usr/bin/qbittorrent and rebooted and still nothing.

I am using nano to save crontab, is this valid? It tells me it installs it. Is @reboot correct, is what I put after it correct?

I read that an empty line has to follow the jobs and I have an empty line after @reboot ~/Documents/rtorrent_cron.

---

### Post by usalug on 2012-10-03
@reboot ~/Documents/rtorrent_cron  is fine......however use the full path. and not the ~/ 

is rtorrent_cron executable ?
ls -lah ~/Documents/rtorrent_cron
what's the output ?

---

### Post by von Stalhein on 2012-10-04
I've had a similar problem the last two installs (12.04 & 11.10). Prior to that since 7.04 there have been no issues.

Whatever I've tried to get crontab to work has failed, either via cli or in the GUI.

For instance, the present one I'd like to use is:
```
# m h  dom mon dow   command
59 01 * * * usr/bin/qbittorrent
01 08 * * * killall usr/bin/qbittorrent

```It will not start automatically. The commands work in Terminal both individually or with full path.
It would be terrific if something obvious in the commands could be pointed out :mad: 
Thx.

---

### Post by GRX13 on 2012-10-04
sudo chmod +x rtorrent_cron

[QUOTE=ls -lah rtorrent_cron]-rwxrwxrwx 1 grx grx 905 Sep 29 19:18 rtorrent_cron[/QUOTE]

# m h  dom mon dow   command
@reboot /usr/bin/qbittorrent
@reboot /home/grx/Documents/rtorrent_cron


What's going on?

@reboot clearly isn't working. I uninstalled anacron and now I have:

# m h  dom mon dow   command
* * * * * /usr/bin/qbittorrent
* * * * * /home/grx/Documents/rtorrent_cron

I don't have a /etc/cron, there are no cron daemon entries in task manager, should there be? I'm getting annoyed. It should really be straight forward starting things on start up. I keep starting cron but keep being told it's running. What's this thing about PATH and MAILTO? What. My rtorrent_cron script has #! /bin/bash at the beginning.

---

### Post by GRX13 on 2012-10-04
Please respond.

[IMG]http://i.imgur.com/oNVsu.png[/IMG]

---

### Post by GRX13 on 2012-10-09
Never mind got it working.

* * * * * DISPLAY=*:0.0* qbittorrent

Did the trick. The rtorrent script needs some command line arguments before it will work for me but it works the same but minus the DISPLAY thing.

---

