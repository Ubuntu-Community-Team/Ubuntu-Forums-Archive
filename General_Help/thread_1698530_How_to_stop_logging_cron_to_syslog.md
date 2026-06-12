---
title: "How to stop logging cron to syslog"
date: 2011-03-02
forum: General Help
---

### Post by Trismegister on 2011-03-02
There was a discussion posted here  around two years back that I've just found useful and wanted to add to.

The discussion was "how to stop logging cron to syslog"

The useful answer is to update the line targeting syslog in [FONT="Courier New"]/etc/syslog.conf[/FONT] to say something like:
```
*.*;auth,authpriv.none,mail.none,cron.none -/var/log/syslog
```
the significant part being that [FONT="Courier New"]cron.none[/FONT] means that cron will not log to syslog.

There was discussion about whether this was a good thing to do, but omitted to suggest that adding/ uncommenting the following line  would mean that no information would be lost but that syslog would be less cluttered as a source of monitoring info:

```
cron.*  -/var/log/cron.log
```
You've still got all your cron-related log items available in cron.log if and when you need them


To make the new[FONT="Courier New"] /etc/syslog.con[/FONT]f lines effective you should also, with root privileges:
```
touch /var/log/cron.log
chown syslog:adm /var/log/cron.log
```

and restart syslog. In my case:
```
/etc/init.d/sysklogd restart
```

---

### Post by geoffmcc on 2011-03-02
Please tell me this will stop all the 

>  CRON[1549]: pam_unix(cron:session): session closed for user root


lines in auth.log!

I had previously setup server to send me email notifications on login and sudo and that line kept on causing mass emails and it got pretty annoying.

But it seems by your post only effects syslog

---

### Post by Trismegister on 2011-03-02
@geoffmcc since you are talking about entries in auth.log then the answer has to  be no.

You can change what goes to auth.log by changing the line:
```
auth,authpriv.*          -/var/log/auth.log
``` 
but again, I would't want to lose any information from auth.log myself.

Usually with these services you can change the LogLevel to filter out low-level diagnostics.

Where have you set up your email notifications?

---

### Post by geoffmcc on 2011-03-02
Yea i dont want to loose the info, just put all the cron's in a auth-cron.log or something cause they fill it up alot.

I tried a few different things.

First i tried adding in .bashrc but then i realised could be easily removed.

so then i moved on to (cant remember its name now) but it was a service that you setup to monitor auth.log (others as well) and then in the .conf file you have to tell it what to look for.

Thats when i started to get all the cron emails

so i decided to move onto splunk, but couldnt get emails to get sent. Think its cause i use ssmtp and couldnt find any reference to using splunk with ssmtp.

---

### Post by Trismegister on 2011-03-02
Sorry @geoffmcc, I can't help wiith the specifics of the situation you describe. 

Have you seen [this]("http://www.johnandcailin.com/blog/john/how-setup-real-time-email-notification-critical-syslog-events")? It might be relevant.

I'd be interested in your solution. :)

---

