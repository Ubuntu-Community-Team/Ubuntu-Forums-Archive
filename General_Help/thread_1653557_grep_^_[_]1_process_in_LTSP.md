---
title: "grep ^ [ ]*1 process in LTSP"
date: 2010-12-27
forum: General Help
---

### Post by pravindra.kumar on 2010-12-27
Hi All,
Happy New Year in advance!!

I am facing problem with my LTSP that one process is consuming 100% of CPU for every logged-in users, i run the HTOP and found "grep ^ [ ]*1 process". due to this load average is going upto 7.

pls help.

thanks & regards,
Pravindra Kumar

---

### Post by pravindra.kumar on 2010-12-27
There is output of grep:-

root@iklltsp:/bin# ps -ef |grep grep
1015      4596  5935  0 15:14 ?        00:00:00 /bin/sh -c ps ax| grep "^[ ]*1"
1015      4599  4596  0 15:14 ?        00:00:00 grep ^[ ]*1
deepaks   4603 22942  0 15:14 ?        00:00:00 /bin/sh -c ps ax| grep "^[ ]*1"
veenaw    4604 24718  0 15:14 ?        00:00:00 /bin/sh -c ps ax| grep "^[ ]*1"
quality1  4607 14100  0 15:14 ?        00:00:00 /bin/sh -c ps ax| grep "^[ ]*1"
deepaks   4609  4603  0 15:14 ?        00:00:00 grep ^[ ]*1
quality1  4610  4607  0 15:14 ?        00:00:00 grep ^[ ]*1
1005      4611  2277  0 15:14 ?        00:00:00 /bin/sh -c ps ax| grep "^[ ]*1"
1005      4613  4611  0 15:14 ?        00:00:00 grep ^[ ]*1
root      4615 25907  0 15:14 pts/3    00:00:00 grep grep
veenaw    4616 10066  0 15:14 ?        00:00:00 /bin/sh -c ps ax| grep "^[ ]*1"
veenaw    4618  4616  0 15:14 ?        00:00:00 grep ^[ ]*1
veenaw    4622  4604  0 15:14 ?        00:00:00 grep ^[ ]*1
shashi    4626 13941  0 15:14 ?        00:00:00 /bin/sh -c ps ax| grep "^[ ]*1"
tanuj     4628  2892  0 15:14 ?        00:00:00 /bin/sh -c ps ax| grep "^[ ]*1"
tanuj     4630  4628  0 15:14 ?        00:00:00 grep ^[ ]*1
shashi    4631  4626  0 15:14 ?        00:00:00 grep ^[ ]*1
1050      4632  6069  0 15:14 ?        00:00:00 /bin/sh -c ps ax| grep "^[ ]*1"
1050      4634  4632  0 15:14 ?        00:00:00 grep ^[ ]*1

---

