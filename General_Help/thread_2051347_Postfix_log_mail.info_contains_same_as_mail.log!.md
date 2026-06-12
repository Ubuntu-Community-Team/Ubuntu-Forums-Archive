---
title: "Postfix log mail.info contains same as mail.log?!"
date: 2012-09-01
forum: General Help
---

### Post by MorningSleeper on 2012-09-01
Using 12.04, in /etc/rsyslog.d/50-default.conf I have the following two selectors.

```

mail.*				-/var/log/postfix/mail.log
mail.info			-/var/log/postfix/mail.info

```

As you can see both with a facility of mail and one has * as a priority and the other has info.

The one with a * reports all priorities to the mail.log file as I would expect but the one with just the info priority writes all priority lines to its file like the first one resulting in two log files containing the same info?! How do I get a log file containing just priority level info type lines written to it?

---

### Post by MorningSleeper on 2012-09-02
Nevermind, I just read that when you specify a priority it includes not only messages at that priority but all above it as well which in this case would include everything except for debug since the following is the order of priorities.

debug, info, notice, warning, err, crit, alert, emerg 

So technically the two files should be different as mail.* would include the debug info while mail.info should not. I have not yet tested this.  To restrict to just one priority preceed the priority with a = sign such as mail.=info to get just info related messages.

[http://www.rsyslog.com/doc/rsyslog_conf_filter.html](http://www.rsyslog.com/doc/rsyslog_conf_filter.html)

---

### Post by TheFu on 2012-09-02
That's what mine looks like.  Haven't touched the mail config in years.

If you care, read the syslog man page.  I didn't, but would expect that the different log levels would be put into .info, .warn, .err files and that all logs would be placed into .* files.

.err files would be shortest. 
.warn files would be a little longer, since they contain all the warnings AND all the errors.
.info files would be the longest.

For security reasons, it might be useful to allow more access to the .err files on a system.  I'm pretty sure there's a historical reason these are setup this way. Probably from the 1980s.

---

### Post by MorningSleeper on 2012-09-02
Thanks for the reply, the thing that confused me is I did not realize a priority included all above it. Below is what I am testing.

```
# all priorities
mail.*				-/var/log/postfix/mail.log

# only priorities of info and notice.
mail.info;mail.!=warning	-/var/log/postfix/mail.info

# only priorities of warnings
mail.=warning			-/var/log/postfix/mail.warn

# priorities of err or higher (err, crit, alert, emerg)
mail.err			/var/log/postfix/mail.err

```

---

### Post by dcstar on 2012-09-03
> **TheFu said:**
> 
.........
For security reasons, it might be useful to allow more access to the .err files on a system.  I'm pretty sure there's a historical reason these are setup this way. Probably from the 1980s.

The primary issue here is that Postfix/Sendmail may behave differently to the (many) other SMTP servers available, and the log config has to be set up in that way to allow for programs that send out log data differently.

---

