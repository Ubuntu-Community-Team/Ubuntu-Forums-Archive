---
title: "duplicate syslog messages"
date: 2009-07-08
forum: General Help
---

### Post by allyour80211b on 2009-07-08
Hello all,

I have just configured a Cisco PIX to send syslog messages to my linux box 
[Linux ibex 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 22:12:12 UTC 2009 x86_64 GNU/Linux]

everything is working but I am getting duplicate messages in /var/log/messages as well as my new file /var/log/pix.log

Here is syslog.conf I feel pretty sure this is where my problem is:

==========================================================
#  /etc/syslog.conf	Configuration file for syslogd.
#
#			For more information see syslog.conf(5)
#			manpage.

#
# First some standard logfiles.  Log by facility.
#

auth,authpriv.*			/var/log/auth.log
*.*;auth,authpriv.none		-/var/log/syslog
#cron.*				/var/log/cron.log
daemon.*			-/var/log/daemon.log
kern.*				-/var/log/kern.log
lpr.*				-/var/log/lpr.log
mail.*				-/var/log/mail.log
user.*				-/var/log/user.log

#
# Logging for the mail system.  Split it up so that
# it is easy to write scripts to parse these files.
#
mail.info			-/var/log/mail.info
mail.warning			-/var/log/mail.warn
mail.err			/var/log/mail.err

# Logging for INN news system
#
news.crit			/var/log/news/news.crit
news.err			/var/log/news/news.err
news.notice			-/var/log/news/news.notice

#
# Some `catch-all' logfiles.
#
*.=debug;\
	auth,authpriv.none;\
	news.none;mail.none	-/var/log/debug
[B]*.=info;*.=notice;*.=warning;\
	auth,authpriv.none;\
	cron,daemon.none;\
	mail,news.none		-/var/log/messages[/B]

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
#	*.=notice;*.=warning	/dev/tty8

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
	*.=notice;*.=warning	|/dev/xconsole

[B]# Added 07/08/09 wow that won't happen again for a while.
local3.*   /var/log/pix.log[/B]
===============================

Now I would like the message that normally go to /var/log/messages to continue, but not the PIX messages, they should go to /var/log/pix.log.

from the PIX:
================
FW# sh config | grep logging
logging enable
logging timestamp
logging buffer-size 250000
logging buffered warnings
logging trap notifications
logging asdm warnings
logging facility 19
logging host inside 172.16.8.111
logging permit-hostdown
=================================

172.16.8.111 is my ibex host.  It's this bit I'm nearly sure, I just don't understand the syntax:

============================
[B]*.=info;*.=notice;*.=warning;\
	auth,authpriv.none;\
	cron,daemon.none;\
	mail,news.none		-/var/log/messages[/B]
=====================================================

thanks
ayb

---

