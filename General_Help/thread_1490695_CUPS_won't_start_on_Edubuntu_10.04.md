---
title: "CUPS won't start on Edubuntu 10.04"
date: 2010-05-22
forum: General Help
---

### Post by feed5000 on 2010-05-22
I've installed Edubuntu 10.04. When I went to configure my printer (Administration > Printing), I found the "New" button disabled.

Looking around, I found that CUPS is indeed installed, but not running. So I tried to start it up on the command line. The command results in [ OK ]. But status is consistently "cupsd is not running." And the CUPS error log is not yet created. For all of this, see code below.

Anyone know why CUPS won't start for me?

```

sysadmin@COMP0047:~$ sudo /etc/init.d/cups start
[sudo] password for sysadmin: 
 * Starting Common Unix Printing System: cupsd                           [ OK ] 
sysadmin@COMP0047:~$ sudo /etc/init.d/cups status
Status of Common Unix Printing System: cupsd is not running.
sysadmin@COMP0047:~$ sudo /etc/init.d/cups restart
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 
sysadmin@COMP0047:~$ sudo /etc/init.d/cups status
Status of Common Unix Printing System: cupsd is not running.
sysadmin@COMP0047:~$ /var/log/cups/error_log | gedit
bash: /var/log/cups/error_log: No such file or directory

```

---

