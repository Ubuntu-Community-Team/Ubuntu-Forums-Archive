---
title: "Cron is not working for me"
date: 2012-03-01
forum: General Help
---

### Post by andyklaj1985 on 2012-03-01
Hey Guys

For some reason I can not get crontab to work properly
andrew.

this is what I have put into my cron file (when i type sudo crontab -e): [http://pastebin.com/srUTYTEH](http://pastebin.com/srUTYTEH)

This is the latest log of my /var/log/syslog: [http://pastebin.com/QugFSVkQ](http://pastebin.com/QugFSVkQ)

I run crontab with this sudo crontab and confirm that it is running with ps -ef

As I understand firefox should be opening once a minute but nothing is happening

Could someone help me out?

Kind regards

Andrew

---

### Post by papibe on 2012-03-01
Hi andyklaj1985.

cron has a very limited environment not as rich as a regular bash. If you want to launch a GUI application you need to include the variable DISPLAY.

For instance:
```
*/1 * * * * env DISPLAY=:0 /usr/bin/firefox
```
Note that this will launch firefox every minute (not practical, but good for testing).

For more details on crontab take a look at this [tutorial]("https://help.ubuntu.com/community/CronHowto").

Hope it helps, and tell us how it goes.
Regards.

---

### Post by azmyth on 2012-03-01
Probably the best way to restart cron after changes is to:

sudo service cron restart

---

### Post by andyklaj1985 on 2012-03-01
Hey guys

Thanks a lot for the help!

It works perfectly (I went through that tutorial just not as carefully as I should have!)

Thanks again for the help

Kind regards

Andrew

---

