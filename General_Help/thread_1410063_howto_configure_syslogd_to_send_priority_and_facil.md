---
title: "howto configure syslogd to send priority and facility information?"
date: 2010-02-18
forum: General Help
---

### Post by graricioglu on 2010-02-18
hi all,
 
i want to use an ubuntu server (2.6.31-17-generic #54-Ubuntu SMP) as the central syslog server but the syslog messages does not show the priority and facility information in ubuntu. priority and facility are shown in aix by default and i have many aix servers can be used as the central syslog server, but i prefer using ubuntu if it can provide me these details. 
 
thanks in advance,
Gokhan

---

### Post by rnerwein on 2010-02-18
hi
did you looked in /etc/rsyslog.d/50-default.conf
see also: man rsyslog.conf

i guess that will help you
ciao

---

### Post by graricioglu on 2010-02-19
hi,
 
first of all thank you for the reply. I checked the /etc/rsyslog.d/50-default.conf file and man syslog.conf (man page for rsyslog.conf has not been installed) but there is no information explaining how to print priority and facility information in the syslog messages.
gokhan,

---

### Post by rnerwein on 2010-02-19
hi
sorry it's not rsyslogd.conf it is:  man rsyslog.conf
ciao

---

