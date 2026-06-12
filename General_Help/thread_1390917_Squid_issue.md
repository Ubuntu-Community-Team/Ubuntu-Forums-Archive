---
title: "Squid issue"
date: 2010-01-26
forum: General Help
---

### Post by adeelm on 2010-01-26
Hi,

    I am new at Ubuntu (9.04) and I am configuring Squid on Ubuntu. When I run the following command, I get the th result given below.

[SIZE=3]:~$ sudo service squid reload[/SIZE] 
[sudo] password for abc: 
 * Reloading Squid configuration files
2010/01/26 17:37:12| parseConfigFile: squid.conf:613 unrecognized: '    #change'
2010/01/26 17:37:12| parseConfigFile: squid.conf:648 unrecognized: '    #change'
   ...done.


Please some one tell me the meaning of this _parseConfigFile _becaue I can not understant it.

Thank you all

Adeel

---

### Post by t4thfavor on 2010-01-26
There is a malformed line in the config file. parseConfigFile is just aditing that file for syntax, and has found some errors.

If you wan't to fix it read the file, and go to lines 613, and 648 where the errors are indicated, and you will find something that doesn't quite look right.

---

### Post by adeelm on 2010-02-05
Thank you t4thfavor

It worked..

Adeel

---

