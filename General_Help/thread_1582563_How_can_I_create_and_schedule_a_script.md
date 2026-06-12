---
title: "How can I create and schedule a script?"
date: 2010-09-26
forum: General Help
---

### Post by Robotman on 2010-09-26
I'm running LXDE in Ubuntu 10.04, and NTP won't work properly for me.  I've found that this command in a terminal will set my clock properly:
```
sudo ntpdate time.nrc.ca
```
But I have to do that manually.
How would I go about creating a shell script with that command and then scheduling it to run once a day?

---

### Post by The Cog on 2010-09-26
That's the kind of thing you would do in a cron job. cron is the service that runs jobs at a predetermined regular time. 

To run the command at 01:30 every morning, add a line like this to the file /etc/crontab:
> 30 1 * * * root /usr/sbin/ntpdate time.nrc.ca
There's a thing called anacron that deals with things that cron missed because the PC wasn't running at the time, but I don't know the details f that.

---

### Post by Robotman on 2010-09-27
That did the trick!  Thanks a lot. ;)

---

