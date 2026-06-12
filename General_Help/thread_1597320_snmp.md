---
title: "snmp"
date: 2010-10-15
forum: General Help
---

### Post by g.badawi on 2010-10-15
root@server-desktop:~# cfgmaker --global 'WorkDir:/var/www/mrtg' --global 'Options[_]: bits,growright' --output /etc/mrtg/mrtg.cfg [EMAIL="public@172.18.1.2"]public@172.18.1.2[/EMAIL]
SNMP Error:
no response received
SNMPv1_Session (remote host: "172.18.1.2" [172.18.1.2].161)
community: "public"
request ID: -769512845
PDU bufsize: 8000 bytes
timeout: 2s
retries: 5
backoff: 1)
at /usr/share/perl5/SNMP_util.pm line 629
SNMPWALK Problem for 1.3.6.1.2.1.1 on public@172.18.1.2::::::v4only
at /usr/bin/cfgmaker line 957
WARNING: Skipping [EMAIL="public@172.18.1.2"]public@172.18.1.2[/EMAIL]: as no info could be retrieved
root@server-desktop:~# ps -e |grep snmp
root@server-desktop:~# exit
logout
server@server-desktop:~$

---

