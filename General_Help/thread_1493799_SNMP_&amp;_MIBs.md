---
title: "SNMP &amp; MIBs"
date: 2010-05-26
forum: General Help
---

### Post by pmsumner on 2010-05-26
I'm going a bit mad here, I think I've missed something..

I'm doing SNMP requests to a server, and if I do this:

```
snmpget -m+ALL -cpublic -v2c philsdvip netvu.netvuHealthMon.adMemory.memTotalHeap.0
```

It works, I get the result I expect.  This also works if I do:

```
export MIBS=+ALL
```

From the command line and leave the "-m+ALL" off the command line.

I think this proves I have the MIBS in the right place (/usr/share/snmp/mibs/)

Without the MIBS variable set to "+ALL", I get this:
```
dm@tsg-cacti:~$ snmpget -cpublic -v2c philsdvip .netvu.netvuHealthMon.adMemory.memTotalHeap.0
.netvu.netvuHealthMon.adMemory.memTotalHeap.0: Unknown Object Identifier (Sub-id not found: (top) -> netvu)
```


This is no good, as I am trying to use a web based tool to monitor the servers and I can't change the request to have "-m+ALL" on the command and don't want to set the MIBS variable for the web server user.  I can use the numberic OIDs but would much rather not have to.

I have tried putting "mibs +ALL" into a new file - /etc/snmp/snmp.conf - this didn't succeed at all - the behaviour didn't change.

Can anyone suggest what I've done wrong and how to make it right?

---

### Post by dino99 on 2010-05-26
the programming forum might be better for help, sorry its over my skills

---

### Post by pmsumner on 2010-05-28
I've sorted it.  I found that you can set environment variables for the apache user in:

/etc/apache2/envvars

Added MIBS=+ALL there, restarted apache and it works!

---

