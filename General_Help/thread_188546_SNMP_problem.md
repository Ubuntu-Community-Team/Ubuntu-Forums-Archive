---
title: "SNMP problem"
date: 2006-06-04
forum: General Help
---

### Post by Eklöf on 2006-06-04
Hi. I've installed snmpd and cacti for logging some stats on the server. Now it seems I can'textract ethernet information and I think it's because not all the mibs are "installed" or something. 

This is what i getfrom a snmpwalk.A friend of mine have lots more on his debian system. How do I install the missing ones ?





jonas@trimix:~$ snmpwalk -cpublic -v 1 localhost
SNMPv2-MIB::sysDescr.0 = STRING: Linux trimix 2.6.15-23-server #1 SMP Tue May 23 15:10:35 UTC 2006 i686SNMPv2-MIB::sysObjectID.0 = OID: NET-SNMP-MIB::netSnmpAgentOIDs.10
SNMPv2-MIB::sysUpTime.0 = Timeticks: (17930915) 2 days, 1:48:29.15
SNMPv2-MIB::sysContact.0 = STRING: Root <root@localhost> (configure /etc/snmp/snmpd.local.conf)
SNMPv2-MIB::sysName.0 = STRING: trimix
SNMPv2-MIB::sysLocation.0 = STRING: Unknown (configure /etc/snmp/snmpd.local.conf)
SNMPv2-MIB::sysORLastChange.0 = Timeticks: (13) 0:00:00.13
SNMPv2-MIB::sysORID.1 = OID: IF-MIB::ifMIB
SNMPv2-MIB::sysORID.2 = OID: SNMPv2-MIB::snmpMIB
SNMPv2-MIB::sysORID.3 = OID: TCP-MIB::tcpMIB
SNMPv2-MIB::sysORID.4 = OID: IP-MIB::ip
SNMPv2-MIB::sysORID.5 = OID: UDP-MIB::udpMIB
SNMPv2-MIB::sysORID.6 = OID: SNMP-VIEW-BASED-ACM-MIB::vacmBasicGroup
SNMPv2-MIB::sysORID.7 = OID: SNMP-FRAMEWORK-MIB::snmpFrameworkMIBCompliance
SNMPv2-MIB::sysORID.8 = OID: SNMP-MPD-MIB::snmpMPDCompliance
SNMPv2-MIB::sysORID.9 = OID: SNMP-USER-BASED-SM-MIB::usmMIBCompliance
SNMPv2-MIB::sysORDescr.1 = STRING: The MIB module to describe generic objects for network interface sub-layers
SNMPv2-MIB::sysORDescr.2 = STRING: The MIB module for SNMPv2 entities
SNMPv2-MIB::sysORDescr.3 = STRING: The MIB module for managing TCP implementations
SNMPv2-MIB::sysORDescr.4 = STRING: The MIB module for managing IP and ICMP implementations
SNMPv2-MIB::sysORDescr.5 = STRING: The MIB module for managing UDP implementations
SNMPv2-MIB::sysORDescr.6 = STRING: View-based Access Control Model for SNMP.
SNMPv2-MIB::sysORDescr.7 = STRING: The SNMP Management Architecture MIB.
SNMPv2-MIB::sysORDescr.8 = STRING: The MIB for Message Processing and Dispatching.
SNMPv2-MIB::sysORDescr.9 = STRING: The management information definitions for the SNMP User-based Security Model.
SNMPv2-MIB::sysORUpTime.1 = Timeticks: (6) 0:00:00.06
SNMPv2-MIB::sysORUpTime.2 = Timeticks: (7) 0:00:00.07
SNMPv2-MIB::sysORUpTime.3 = Timeticks: (7) 0:00:00.07
SNMPv2-MIB::sysORUpTime.4 = Timeticks: (7) 0:00:00.07
SNMPv2-MIB::sysORUpTime.5 = Timeticks: (7) 0:00:00.07
SNMPv2-MIB::sysORUpTime.6 = Timeticks: (7) 0:00:00.07
SNMPv2-MIB::sysORUpTime.7 = Timeticks: (13) 0:00:00.13
SNMPv2-MIB::sysORUpTime.8 = Timeticks: (13) 0:00:00.13
SNMPv2-MIB::sysORUpTime.9 = Timeticks: (13) 0:00:00.13
End of MIB

---

### Post by Eklöf on 2006-06-04
Noone ?

---

### Post by gyterpena on 2008-06-02
same over here

---

### Post by Inwards on 2008-07-11
I have exactly the same issue and it's driving me mad.  It looks like I'm missing MIB modules or something.  They all seem to be present in the /usr/share/snmp/mibs folder, but every tool I try doesn't display any data at all.  Here's what I get from snmpwalk:

inwards@machinder:/usr/share/snmp/mibs$ snmpwalk -v1 -c public localhost
SNMPv2-MIB::sysDescr.0 = STRING: Linux machinder 2.6.24-19-server #1 SMP Wed Jun 18 14:44:47 UTC 2008 x86_64
SNMPv2-MIB::sysObjectID.0 = OID: NET-SNMP-MIB::netSnmpAgentOIDs.10
DISMAN-EVENT-MIB::sysUpTimeInstance = Timeticks: (42545) 0:07:05.45
SNMPv2-MIB::sysContact.0 = STRING: Inwards
SNMPv2-MIB::sysName.0 = STRING: machinder
SNMPv2-MIB::sysLocation.0 = STRING: Terminus
SNMPv2-MIB::sysORLastChange.0 = Timeticks: (0) 0:00:00.00
SNMPv2-MIB::sysORID.1 = OID: SNMP-FRAMEWORK-MIB::snmpFrameworkMIBCompliance
SNMPv2-MIB::sysORID.2 = OID: SNMP-MPD-MIB::snmpMPDCompliance
SNMPv2-MIB::sysORID.3 = OID: SNMP-USER-BASED-SM-MIB::usmMIBCompliance
SNMPv2-MIB::sysORID.4 = OID: SNMPv2-MIB::snmpMIB
SNMPv2-MIB::sysORID.5 = OID: TCP-MIB::tcpMIB
SNMPv2-MIB::sysORID.6 = OID: IP-MIB::ip
SNMPv2-MIB::sysORID.7 = OID: UDP-MIB::udpMIB
SNMPv2-MIB::sysORID.8 = OID: SNMP-VIEW-BASED-ACM-MIB::vacmBasicGroup
SNMPv2-MIB::sysORDescr.1 = STRING: The SNMP Management Architecture MIB.
SNMPv2-MIB::sysORDescr.2 = STRING: The MIB for Message Processing and Dispatching.
SNMPv2-MIB::sysORDescr.3 = STRING: The management information definitions for the SNMP User-based Security Model.
SNMPv2-MIB::sysORDescr.4 = STRING: The MIB module for SNMPv2 entities
SNMPv2-MIB::sysORDescr.5 = STRING: The MIB module for managing TCP implementations
SNMPv2-MIB::sysORDescr.6 = STRING: The MIB module for managing IP and ICMP implementations
SNMPv2-MIB::sysORDescr.7 = STRING: The MIB module for managing UDP implementations
SNMPv2-MIB::sysORDescr.8 = STRING: View-based Access Control Model for SNMP.
SNMPv2-MIB::sysORUpTime.1 = Timeticks: (0) 0:00:00.00
SNMPv2-MIB::sysORUpTime.2 = Timeticks: (0) 0:00:00.00
SNMPv2-MIB::sysORUpTime.3 = Timeticks: (0) 0:00:00.00
SNMPv2-MIB::sysORUpTime.4 = Timeticks: (0) 0:00:00.00
SNMPv2-MIB::sysORUpTime.5 = Timeticks: (0) 0:00:00.00
SNMPv2-MIB::sysORUpTime.6 = Timeticks: (0) 0:00:00.00
SNMPv2-MIB::sysORUpTime.7 = Timeticks: (0) 0:00:00.00
SNMPv2-MIB::sysORUpTime.8 = Timeticks: (0) 0:00:00.00
End of MIB

If I try to query any of the MIBs I get something like:

inwards@machinder:/usr/share/snmp/mibs$ sudo snmpwalk -v2c -c public localhost ip
IP-MIB::ip = No more variables left in this MIB View (It is past the end of the MIB tree)

---

