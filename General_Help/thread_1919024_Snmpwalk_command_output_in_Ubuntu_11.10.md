---
title: "Snmpwalk command output in Ubuntu 11.10"
date: 2012-02-02
forum: General Help
---

### Post by teriyaki-89 on 2012-02-02
Hi i recently installed ubuntu 11.10 and snmp package
So when i query host  on network i use  command like this 
snmpwalk  -v1 127.0.0.1 -c private  .1.3.6.1.4.1.2021.4.6.0

i get output like this 
so.3.6.1.4.1.2021.4.6.0 = INTEGER: 776508

but in previous version of ubuntu i got full ouptut like 
Mem.Avail. INTEGER: 776508
so that i could know what mib i am using

How can i get the full output back ?

---

### Post by Eisenkopf on 2012-02-07
You need to install the package snmp-mibs-downloader.

This package contains a lot of mibs, which will be parsed by snmpwalk.

---

### Post by teriyaki-89 on 2012-02-07
hi thank you for reply i just installed snmp-mibs-downloader
by apt-get install snmp-mibs-downloader

reloaded snmpd
and did env LANG=C mrtg cpu.cfg
same error

Unknown SNMP var ssCpuRawUser.0
 at /usr/bin/mrtg line 2251
Unknown SNMP var ssCpuRawUser.0
 at /usr/bin/mrtg line 2251
2012-02-07 15:28:24: WARNING: Expected a number but got '44 days, 6:32:22'
2012-02-07 15:28:24: WARNING: Expected a number but got 'server2'
Unknown SNMP var ssCpuRawSystem.0
 at /usr/bin/mrtg line 2251
Unknown SNMP var ssCpuRawSystem.0
 at /usr/bin/mrtg line 2251

---

### Post by Eisenkopf on 2012-02-07
ok, seems that mrtg cant resolve the oid ssCpuRawUser.0 which is included in UCD-SNMP-MIB.

can you find this mib on your system?

what does a 'snmpwalk v1 -c yourcommunity localhost' give back?

---

### Post by teriyaki-89 on 2012-02-07
i found my UCD-SNMP-MIB in  /usr/share/mibs/netsnmp/
Now  when i invoke env LANG=C mrtg cpu.cfg i have no error
but the graph still paints nulls  for my Gentoo client, though i used  both mibs in my cpu.cfg

I forgot to tell that SNMP server Debain and SNMP clients are Gentoo servers, so debain client returns right values for MRTG, but gentoo returns nulls

[B]#Target[hb1.cpu]: .1.3.6.1.4.1.2021.11.50.0&.1.3.6.1.4.1.2021.11.50.0private@10.0.18.34
[/B]or[B]
Target[hb1.cpu]: ssCpuRawUser.0&ssCpuRawUser.0private@10.0.18.34  [/B]



Snmpwalk returns 

snmpwalk -v1 -c private 10.0.18.37 .1.3.6.1.4.1.2021.11.50.0
[B]iso.3.6.1.4.1.2021.11.50.0 = Counter32: 860430523

On a russian forum i was advised to try zabbix. I am going to try this. I am very frustrated with MRTG 
[/B]

---

