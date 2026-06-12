---
title: "what is causing this message in /var/log/messages ?"
date: 2009-11-13
forum: General Help
---

### Post by negativ on 2009-11-13
Exactly every 20 minutes, the message
```
-- MARK --
```
is being inserted into /var/log/messages.

I can't figure out where it's coming from.  I've disabled the only crons that aren't there by default.

1.  Does anyone know where "-- MARK --" comes from, OR,
2.  Can anyone tell me how to find out what process is actually creating the log entry?

I'm not exactly /worried/ about it, but I hate not knowing why it's there.


by the way, this is Jaunty.

---

### Post by sisco311 on 2009-11-13
```
man syslogd | less +2/"\-m interval"
```

---

### Post by wojox on 2009-11-13
/etc/rsyslog.conf

```

#  /etc/rsyslog.conf	Configuration file for rsyslog.
#
#			For more information see
#			/usr/share/doc/rsyslog-doc/html/rsyslog_conf.html
#
#  Default logging rules can be found in /etc/rsyslog.d/50-default.conf


#################
#### MODULES ####
#################

$ModLoad imuxsock # provides support for local system logging
$ModLoad imklog   # provides kernel logging support (previously done by rklogd)
#$ModLoad immark  # provides --MARK-- message capability

$KLogPath /var/run/rsyslog/kmsg

# provides UDP syslog reception
#$ModLoad imudp
#$UDPServerRun 514

# provides TCP syslog reception
#$ModLoad imtcp
#$InputTCPServerRun 514


###########################
#### GLOBAL DIRECTIVES ####
###########################

#
# Use traditional timestamp format.
# To enable high precision timestamps, comment out the following line.
#
$ActionFileDefaultTemplate RSYSLOG_TraditionalFileFormat

#
# Set the default permissions for all log files.
#
$FileOwner syslog
$FileGroup adm
$FileCreateMode 0640
$DirCreateMode 0755
$Umask 0022
$PrivDropToUser syslog
$PrivDropToGroup syslog

#
# Include all config files in /etc/rsyslog.d/
#
$IncludeConfig /etc/rsyslog.d/*.conf


```

---

### Post by sisco311 on 2009-11-13
> **wojox said:**
> /etc/rsyslog.conf



yep, in Karmic, rsyslog is the default logging daemon.

anyway,  the logging daemon logs a mark timestamp regularly. the default interval between two -- MARK -- lines is 20  minutes.

---

### Post by negativ on 2009-11-13
> **sisco311 said:**
> ```
man syslogd | less +2/"\-m interval"
```

"no manual entry for syslogd"


but!

that's more clue than I had before, so thanks.

---

