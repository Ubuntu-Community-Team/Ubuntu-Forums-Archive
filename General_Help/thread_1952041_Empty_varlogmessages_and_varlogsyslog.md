---
title: "Empty /var/log/messages and /var/log/syslog"
date: 2012-04-03
forum: General Help
---

### Post by ee99ee on 2012-04-03
Hello. I have a new, clean install of Ubuntu 11.10. There is nothing being logged to either /var/log/messages or /var/log/syslog. I tried enabling the configuration described in post 2 here [http://ubuntuforums.org/showthread.php?t=1728570](http://ubuntuforums.org/showthread.php?t=1728570), but nothing has changed.

Both files are 0 bytes in size.

How do I get my logs back?!

Here is the contents of my /etc/rsyslog.d/50-default.conf

```
#  Default rules for rsyslog.
#
#			For more information see rsyslog.conf(5) and /etc/rsyslog.conf

#
# First some standard log files.  Log by facility.
#
auth,authpriv.*			/var/log/auth.log
*.*;auth,authpriv.none		-/var/log/syslog
#cron.*				/var/log/cron.log
#daemon.*			-/var/log/daemon.log
kern.*				-/var/log/kern.log
#lpr.*				-/var/log/lpr.log
mail.*				-/var/log/mail.log
#user.*				-/var/log/user.log

#
# Logging for the mail system.  Split it up so that
# it is easy to write scripts to parse these files.
#
#mail.info			-/var/log/mail.info
#mail.warn			-/var/log/mail.warn
mail.err			/var/log/mail.err

#
# Logging for INN news system.
#
news.crit			/var/log/news/news.crit
news.err			/var/log/news/news.err
news.notice			-/var/log/news/news.notice

#
# Some "catch-all" log files.
#
*.=debug;\
	auth,authpriv.none;\
	news.none;mail.none	-/var/log/debug
*.=info;*.=notice;*.=warn;\
	auth,authpriv.none;\
	cron,daemon.none;\
	mail,news.none		-/var/log/messages

#
# Emergencies are sent to everybody logged in.
#
*.emerg				*

#
# I like to have messages displayed on the console, but only on a virtual
# console I usually leave idle.
#
#daemon,mail.*;\
#	news.=crit;news.=err;news.=notice;\
#	*.=debug;*.=info;\
#	*.=notice;*.=warn	/dev/tty8

# The named pipe /dev/xconsole is for the `xconsole' utility.  To use it,
# you must invoke `xconsole' with the `-file' option:
# 
#    $ xconsole -file /dev/xconsole [...]
#
# NOTE: adjust the list below, or you'll go crazy if you have a reasonably
#      busy site..
#
daemon.*;mail.*;\
	news.err;\
	*.=debug;*.=info;\
	*.=notice;*.=warn	|/dev/xconsole
```

Thanks!

-Chris

---

### Post by ee99ee on 2012-04-07
Still not working

-Chris

---

