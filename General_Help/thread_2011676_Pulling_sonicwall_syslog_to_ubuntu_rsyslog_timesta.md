---
title: "Pulling sonicwall syslog to ubuntu rsyslog timestamp loses itself"
date: 2012-06-27
forum: General Help
---

### Post by Kashan35 on 2012-06-27
*waves*

Pulling my hair out trying to figure this out.  I am running a sonicwall TZ100 router and using an Ubuntu desktop to pull the logs via UDP to rsyslog

Here is my full rsyslog.conf pulling from the same subnet on a natted IP, logs have been modified to remove all the IP's

The issue I am encountering, is rsyslog timestamp keeps getting fouled up, falling behind via tail -f every second by a couple seconds, 10 minutes of tailing and my logs are 10+ minutes behind.  Soon as I restart rsyslog it logs correctly again.

The timestamp on my /var/log/sonicwall.log is always correct, date on SonicWall and Ubunut desktop are both correct.

> 
#  /etc/rsyslog.conf    Configuration file for rsyslog.
#
#                       For more information see
#                       /usr/share/doc/rsyslog-doc/html/rsyslog_conf.html
#
#  Default logging rules can be found in /etc/rsyslog.d/50-default.conf


#################
#### MODULES ####
#################

$ModLoad imuxsock # provides support for local system logging
$ModLoad imklog   # provides kernel logging support (previously done by rklogd)
#$ModLoad immark  # provides --MARK-- message capability

# provides UDP syslog reception
$ModLoad imudp
$UDPServerRun 514

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
#$ActionFileDefaultTemplate RSYSLOG_TraditionalFileFormat


$ModLoad imudp
$UDPServerRun 514

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
#$ActionFileDefaultTemplate RSYSLOG_TraditionalFileFormat



# Filter duplicated messages
$RepeatedMsgReduction on

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
# Where to place spool files
#
$WorkDirectory /var/spool/rsyslog

#
# Include all config files in /etc/rsyslog.d/
#
$IncludeConfig /etc/rsyslog.d/*.conf


# date
Wed Jun 27 14:00:00 CDT 2012
# cd /var/log
# pwd
/var/log
# rsyslog stop
sh: 27: rsyslog: not found
# service rsyslog stop
rsyslog stop/waiting
# service rsyslog start
rsyslog start/running, process 7516
# tail -f sonicwall.log
2012-06-27T13:19:39.865051-05:00 X id=firewall sn=0017C581219E time="2012-06-27 13:21:29"  fw=xxxx pri=6 c=262144 m=98 msg="Connection Opened" n=4546213  src=X53698:X0 dst=X:443:X0 proto=tcp/https   
2012-06-27T13:19:39.865379-05:00 X id=firewall  sn=0017C581219E time="2012-06-27 13:21:29" fw=X pri=6  c=262144 m=98 msg="Connection Opened" n=4546213  src=X:53699:X0 dst=192.168.4.2:443:X0 proto=tcp/https   
2012-06-27T13:19:39.865379-05:00 X id=firewall  sn=0017C581219E time="2012-06-27 13:21:29" fw=X pri=6  c=262144 m=98 msg="Connection Opened" n=4546213  src=X:53700:X0 dst=X:443:X0 proto=tcp/https   
2012-06-27T13:19:39.865625-05:00 X id=firewall  sn=0017C581219E time="2012-06-27 13:21:29" fw=X pri=6  c=262144 m=98 msg="Connection Opened" n=4546213  src=X:53701:X0 dst=X:443:X0 proto=tcp/https   
2012-06-27T13:19:39.865625-05:00 x id=firewall  sn=0017C581219E time="2012-06-27 13:21:29" fw=X pri=6  c=262144 m=98 msg="Connection Opened" n=4546213  src=X:53702:X0 dst=X:443:X0 proto=tcp/https   
2012-06-27T13:19:39.866073-05:00 X id=firewall  sn=0017C581219E time="2012-06-27 13:21:29" fw=X pri=6  c=262144 m=98 msg="Connection Opened" n=4546213  src=X:53703:X0 dst=X:443:X0 proto=tcp/https   
2012-06-27T13:19:39.875453-05:00 X id=firewall  sn=0017C581219E time="2012-06-27 13:21:29" fw=X pri=6 c=1024  m=97 n=1286264 src=X:51259:X0 dst=X:X1  proto=tcp/http op=GET sent=1374 rcvd=286 result=0 dstname=[www.pandora.com]("http://www.pandora.com") arg=/img/player-controls/progress-left.png  code=64 Category="Not Rated" 
2012-06-27T13:19:39.876763-05:00 192.168.4.1 id=firewall  sn=0017C581219E time="2012-06-27 13:21:29" fw=X pri=6 c=1024  m=97 n=1286265 src=X:51260:X0 dst=X:80:X1  proto=tcp/http op=GET sent=1376 rcvd=287 result=0 dstname=[www.pandora.com]("http://www.pandora.com") arg=/img/player-controls/progress-middle.png  code=64 Category="Not Rated" 
2012-06-27T13:19:39.878486-05:00 X id=firewall  sn=0017C581219E time="2012-06-27 13:21:29" fw=X pri=6 c=1024  m=97 n=1286268 src=X:51261:X0 dst=208.85.40.80:80:X1  proto=tcp/http op=GET sent=1375 rcvd=287 result=0 dstname=[www.pandora.com]("http://www.pandora.com") arg=/img/player-controls/progress-right.png  code=64 Category="Not Rated" 
2012-06-27T13:19:39.878486-05:00 X id=firewall  sn=0017C581219E time="2012-06-27 13:21:29" fw=X pri=6 c=1024  m=97 n=1286268 src=X:51262:X0 dst=X:80:X1  proto=tcp/http op=GET sent=1356 rcvd=288 result=0 dstname=[www.pandora.com]("http://www.pandora.com") arg=/img/skintab_bg.png  code=64 Category="Not Rated" 
2012-06-27T14:00:29.044495-05:00 X id=firewall  sn=0017C581219E time="2012-06-27 14:02:19" fw=X pri=6  c=262144 m=98 msg="Connection Opened" n=4593786  src=X:56624:X0 dst=X:53:X1 proto=udp/dns   
2012-06-27T14:00:29.046577-05:00 X id=firewall  sn=0017C581219E time="2012-06-27 14:02:19" fw=X pri=6  c=262144 m=98 msg="Connection Opened" sess=Web n=4593789 usr="X"  src=X:26558:X0 dst=204.16.230.85:53:X1 proto=udp/dns   
2012-06-27T14:00:29.046577-05:00 X id=firewall  sn=0017C581219E time="2012-06-27 14:02:19" fw=X pri=6  c=262144 m=98 msg="Connection Opened" sess=Web n=4593789 usr="XXXXX"  src=X:26558:X0 dst=X:53:X1 proto=udp/dns   
2012-06-27T14:00:29.046861-05:00 X id=firewall  sn=0017C581219E time="2012-06-27 14:02:19" fw=X pri=6  c=262144 m=98 msg="Connection Opened" sess=Web n=4593789 usr="admin"  src=XX:26558:X0 dst=8.8.8.8:53:X1 proto=udp/dns   
2012-06-27T14:00:29.177278-05:00 XXX id=firewall  sn=0017C581219E time="2012-06-27 14:02:19" fw= pri=6 c=1024  m=537 msg="Connection Closed" f=2 sess=Web n=7724295 usr="admin"  src=X0 dst=8.8.8.8:53:X1 proto=udp/dns sent=168  rcvd=70   
2012-06-27T14:00:29.242203-05:00 192.168.4.1 id=firewall  sn=0017C581219E time="2012-06-27 14:02:19" fw=xxxx pri=6 c=1024  m=537 msg="Connection Closed" n=7724296 src=xxxxx:25586:X1  dst=xxxx:0:X1 proto=udp/0  
Any ideas?  I have no idea what could be causing this, any help would be greatly appreciated

Thanks

Kashan
[IMG]https://mail.google.com/mail/u/0/images/cleardot.gif[/IMG]

---

