---
title: "ports not &quot;open&quot;"
date: 2010-11-21
forum: General Help
---

### Post by Helixit on 2010-11-21
Ubuntu 10.x server
vsftp            mysql
webmin           Apache2

I am running the Ubuntu server on the same 192.169.x.x subnet as the PC I am using to test vsftp and webmin and Apache.

I can connect to the Apache web site hosted on the Ubuntu server but I cannot connect to any other service -- i.e. port 21 or port 10000 or 3306.

Netstat shows:

tcp     0     0 0.0.0.0:3306     0.0.0.0:*     LISTENING
tcp     0     0 0.0.0.0:10000    0.0.0.0:*     LISTENING
tcp6    0     0 :::80            :::*          LISTENING
udp     0     0 0.0.0.0:10000    0.0.0.0:*
udp     0     0 0.0.0.0:68       0.0.0.0:*

service vsftpd start returns:
vsftpd start\running, process 1178

vsftpd.conf shows:
listen=YES
anonymous_user=YES

Just about all of the features of the sample vsftpd.conf file that is included in the package have been un-commented.

wtf? why does vsftpd not listen at port 21? Why can't I use webmin even though it is listening at port 10000?

I'm yet another newbie so kiss please.

Thanks in advance

Al

---

### Post by northern lights on 2010-11-21
Open port 21 via [iptables]("https://help.ubuntu.com/community/IptablesHowTo")

---

### Post by Helixit on 2010-11-21
Yeah, have now removed all entries from iptables (sudo iptables -F and iptables-X) and still nothing.

Al

---

