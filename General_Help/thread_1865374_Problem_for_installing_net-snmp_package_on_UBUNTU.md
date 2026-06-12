---
title: "Problem for installing net-snmp package on UBUNTU"
date: 2011-10-20
forum: General Help
---

### Post by prashantn on 2011-10-20
Hi,
    I am prashant ,  I downloaded the latest package(source) of net-snmp with version:5.7.1 from the link [http://www.net-snmp.org/download.html](http://www.net-snmp.org/download.html)
 
   I started installing the package on UBUNTU with version:2.6.38-8-generic,  by running following   commands
1) ./configure
    This worked fine.
2) make
    This is the problem i faced when i tried to compile it using make, it showed following error after running make:

creating [libnetsnmpagent.la]("http://libnetsnmpagent.la/")
/bin/sed: can't read Related/SNMP_Downloads/net-snmp/net-snmp-5.4.1/snmplib/[libnetsnmp.la]("http://libnetsnmp.la/"): No such file or directory
libtool: link: `Related/SNMP_Downloads/net-snmp/net-snmp-5.4.1/snmplib/[libnetsnmp.la]("http://libnetsnmp.la/")' is not a valid libtool archive
make[1]: *** [[libnetsnmpagent.la]("http://libnetsnmpagent.la/")] Error 1
make[1]: Leaving directory `/home/prashant/Desktop/SNMP_ Related/SNMP_Downloads/net-snmp/net-snmp-5.4.1/agent'
make: *** [subdirs] Error 1


Any one can please help me out.

Thanks and Regards 
Prashant N

---

