---
title: "ARGS in snmpd.conf"
date: 2012-06-05
forum: General Help
---

### Post by lt-mini on 2012-06-05
Hi all, 

I've got a simple and quick questions.

Is it possible to have a variable in the snmpd.conf for the ARGS parameter of an exec function?

exec [MIBOID] NAME PROG ARGS

for example:

*exec check_temp /tmp/check_temp.pl _$processor_*
where _processor_ is a parameter from a script from nagios:
*check_snmp_exec.sh $HOSTADDRESS$ check_temp _proc1_*


Kind Regards

---

