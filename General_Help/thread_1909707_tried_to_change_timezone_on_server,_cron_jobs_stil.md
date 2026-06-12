---
title: "tried to change timezone on server, cron jobs still running on UTC time?"
date: 2012-01-15
forum: General Help
---

### Post by sneakyimp on 2012-01-15
I've allocated a Cloud Server running Ubuntu at rackspace.com.  The server was initially configured to be on UTC time.  As I live in Los Angeles, this was a bit maddening when trying to determine what times cron jobs should run (this machine cooperates with another server in the United States).  I therefore went through the trouble of changing the time on the server by doing this:
```
apt-get install ntp
dpkg-reconfigure tzdata  // this launches a wizard

```

Now, when I type the **date** command on my server via ssh, it reflects the same time and timezone as my ubuntu desktop here in los angeles:
```
root@server:~# date
Sun Jan 15 16:29:20 PST 2012
```

The problem is that I have a cron job set up to run at 23:00 hours (11pm) but it is running at 15:00 hours los angeles time.  Unless I'm mistaken, that's equal to 23:00 UTC, right?  Seems to me that somehow the cron jobs are unaffected by my date changes above and for some reason the times I specify in my crontab are still in UTC.  WTF?  How do I fix this?

Here's the crontab.  This script fired off at 3pm california time today:
```
# restart the ImageDaemon each day at 11p PST
0 23 * * * php -q /root/my_script.php > /root/cron_output.txt
```

---

### Post by papibe on 2012-01-15
Have tried to restart the cron deamon?
```
sudo service cron restart
```
Just an idea.
Regards.

---

### Post by sneakyimp on 2012-01-17
> **papibe said:**
> Have tried to restart the cron deamon?
```
sudo service cron restart
```
Just an idea.
Regards.

That appears to have solved the problem Thank you very much!

---

