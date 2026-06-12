---
title: "cisco installs but don´t work"
date: 2006-03-09
forum: General Help
---

### Post by BPM on 2006-03-09
hy@all,

i installed the client from cisco (version 4.7).
installation works fine but when i try to connest i got:

bpm@kubuntu:~/install/vpnclient$ vpnclient connect aon
Cisco Systems VPN Client Version 4.7.00 (0640)
Copyright (C) 1998-2005 Cisco Systems, Inc. All Rights Reserved.
Client Type(s): Linux
Running on: Linux 2.6.12-10-686-smp #1 SMP Mon Jan 16 18:39:17 UTC 2006 i686
Config file directory: /etc/opt/cisco-vpnclient


there is no more output in the console and nothing happens.

whats wrong?

please help me!!

regards
markus

---

### Post by John.Michael.Kane on 2006-03-09
[http://www.siliconvalleyccie.com/cisco-hn/dsl-pix.htm](http://www.siliconvalleyccie.com/cisco-hn/dsl-pix.htm)
[http://www.siliconvalleyccie.com/cisco-hn/dsl-router.htm](http://www.siliconvalleyccie.com/cisco-hn/dsl-router.htm)
[http://www.siliconvalleyccie.com/cisco-hn/vpn-cisco.htm](http://www.siliconvalleyccie.com/cisco-hn/vpn-cisco.htm)
[http://www.mcmaster.ca/uts/network/vpn/vpnclient_linux.htm](http://www.mcmaster.ca/uts/network/vpn/vpnclient_linux.htm)

---

### Post by sublime on 2006-03-09
make sure that you start the client before you try to connect.  sudo /etc/init.d/vpnclient_init start  then you can connect.

---

### Post by BPM on 2006-03-10
thx for your quick answer.

the client is startet:
bpm@kubuntu:~$ sudo /etc/init.d/vpnclient_init start
Starting /opt/cisco-vpnclient/bin/vpnclient: Done
bpm@kubuntu:~$ sudo vpnclient connect aon
Cisco Systems VPN Client Version 4.7.00 (0640)
Copyright (C) 1998-2005 Cisco Systems, Inc. All Rights Reserved.
Client Type(s): Linux
Running on: Linux 2.6.12-10-686-smp #1 SMP Mon Jan 16 18:39:17 UTC 2006 i686
Config file directory: /etc/opt/cisco-vpnclient

nothing more to see in the console.

my profile:
[main]
Description=Verbinden mit aon
Host=.........
AuthType=1
GroupName=........
GroupPwd=................
EnableISPConnect=0
ISPConnectType=0
ISPConnect=
ISPCommand=
Username=...........
UserPassword=.......
SaveUserPassword=0
EnableBackup=0
BackupServer=
EnableNat=1
CertStore=0
CertName=
CertPath=
CertSubjectName=
DHGroup=2
ForceKeepAlives=0
TunnelingMode=1
TCPTunnelingPort=443


any idea?

regards
markus

---

