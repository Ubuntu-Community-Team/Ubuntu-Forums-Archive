---
title: "Ubuntu-equivalent for /var/log/messages?"
date: 2011-09-18
forum: General Help
---

### Post by hugocoolens on 2011-09-18
I have been a longtime Debian user, so switching to Ubuntu makes me look now and then for equivalents to get certain things done. One thing I'm missing is the file /var/log/messages, I use this when attaching new hardware to see what's happening: tail -f /var/log/messages
To my surprise Ubuntu doesn't seem to have this file, how can I get the same info I got on my Debian-machines using Ubuntu?

thanks in advance
hugo

---

### Post by howefield on 2011-09-18
Have a browse at this thread..


[http://ubuntuforums.org/showthread.php?t=1728570](http://ubuntuforums.org/showthread.php?t=1728570)

---

### Post by haqking on 2011-09-18
> **hugocoolens said:**
> I have been a longtime Debian user, so switching to Ubuntu makes me look now and then for equivalents to get certain things done. One thing I'm missing is the file /var/log/messages, I use this when attaching new hardware to see what's happening: tail -f /var/log/messages
To my surprise Ubuntu doesn't seem to have this file, how can I get the same info I got on my Debian-machines using Ubuntu?

thanks in advance
hugo

Depends on your version, i have 10.10 and have the /var/log/message.

I believe in 11.04 is is disbaled and you have re-enable it.

```
cat /etc/rsyslog.d/50-default.conf
```and see if the message.log reference is commented out, if so then remove the comment

---

