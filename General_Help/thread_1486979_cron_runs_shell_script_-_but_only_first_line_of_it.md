---
title: "cron runs shell script - but only first line of it"
date: 2010-05-18
forum: General Help
---

### Post by rayhaque on 2010-05-18
Hello folks,

I have a cron job that runs a shell script.  But it only runs the first line of that shell script and not the rest of the file.  I'm a little stumped as to why.  If I run the shell script manually, it runs and executes every single line as it should.

I think I must need some additional syntax to make this run correctly?

Here is the crontab ...
```
root@kchlinux:~/macs# crontab -l
# m h  dom mon dow   command
0 0/2 * * * /root/macs/macdumps.sh > /dev/null # Dump MAC addresses from switches every two hours
```

And here is the shell script that it's running ...
```
root@publiclinux:~/macs# cat macdumps.sh
#!/bin/bash
/usr/bin/perl /root/macs/cammer_c.pl public@10.0.45.1 public@10.0.45.1 > /root/macs/macdump.csv
/usr/bin/perl /root/macs/cammer_c.pl public@10.0.45.1 public@10.0.45.10 >> /root/macs/macdump.csv
/usr/bin/perl /root/macs/cammer_c.pl public@10.0.45.1 public@10.0.44.2 >> /root/macs/macdump.csv
/usr/bin/perl /root/macs/cammer_c.pl public@10.0.45.1 public@10.0.44.233 >> /root/macs/macdump.csv
/usr/bin/perl /root/macs/cammer_c.pl public@10.0.45.1 public@10.0.44.234 >> /root/macs/macdump.csv
/usr/bin/perl /root/macs/cammer_c.pl public@10.0.45.1 public@10.0.44.235 >> /root/macs/macdump.csv
/usr/bin/perl /root/macs/cammer_c.pl public@10.0.45.1 public@10.0.44.236 >> /root/macs/macdump.csv
/usr/bin/perl /root/macs/cammer_c.pl public@10.0.45.1 public@10.0.45.11 >> /root/macs/macdump.csv
/usr/bin/perl /root/macs/cammer_c.pl public@10.0.45.1 public@10.0.45.111 >> /root/macs/macdump.csv
/usr/bin/perl /root/macs/cammer_c.pl public@10.0.45.1 public@10.0.45.12 >> /root/macs/macdump.csv
/usr/bin/perl /root/macs/cammer_c.pl public@10.0.45.1 public@10.0.45.13 >> /root/macs/macdump.csv
/usr/bin/perl /root/macs/cammer_c.pl public@10.0.45.1 public@10.0.45.14 >> /root/macs/macdump.csv
/usr/bin/perl /root/macs/cammer_c.pl public@10.0.45.1 public@10.0.45.15 >> /root/macs/macdump.csv
/usr/bin/perl /root/macs/cammer_c.pl public@10.0.45.1 public@10.0.45.18 >> /root/macs/macdump.csv
/usr/bin/perl /root/macs/cammer_c.pl public@10.0.45.1 public@10.0.45.5 >> /root/macs/macdump.csv
/usr/bin/perl /root/macs/cammer_c.pl public@10.0.45.1 public@10.0.45.6 >> /root/macs/macdump.csv
/usr/bin/perl /root/macs/cammer_c.pl public@10.0.45.1 public@10.0.45.7 >> /root/macs/macdump.csv
/usr/bin/perl /root/macs/cammer_c.pl public@10.0.45.1 public@10.0.45.8 >> /root/macs/macdump.csv
/usr/bin/perl /root/macs/cammer_c.pl public@10.0.45.1 public@10.0.44.243 >> /root/macs/macdump.csv
/bin/grep 10. /root/macs/macdump.csv > /data/log/macs/macdump.csv

```

And here is some version information:
```
root@kchlinux:~/macs# uname -a
Linux kchlinux 2.6.31-14-generic-pae #48-Ubuntu SMP Fri Oct 16 15:22:42 UTC 2009 i686 GNU/Linux
root@kchlinux:~/macs# cat /etc/debian_version
squeeze/sid

```

This is Ubuntu Server!

Any help you can offer me is greatly appreciated.

Thanks!
-Ray Dios Haque

---

### Post by sedawk on 2010-05-18
First change your cron job so it writes a log file and not
to /dev/null.
```
0 0/2 * * * /root/macs/macdumps.sh >/var/tmp/macdumps.log 2>&1 
```

Then you can tell bash to be more verbose about what it does
by adding a line "set -x":
```

#!/bin/bash
set -x
/usr/bin/perl ...

``` 

See the output at /var/tmp/macdumps.log

---

### Post by rayhaque on 2010-05-18
> **sedawk said:**
> First change your cron job so it writes a log file and not
to /dev/null.

Well that's odd.  After changing it to write to a log file, it ran the entire script like it's supposed to.  I suppose it could have also had something to do with raising the bash verbosity as I did that too.

Either way - that fixed it.  Thanks man!

---

