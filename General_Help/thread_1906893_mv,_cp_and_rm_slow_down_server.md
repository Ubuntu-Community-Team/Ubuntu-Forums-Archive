---
title: "mv, cp and rm slow down server"
date: 2012-01-10
forum: General Help
---

### Post by marjenni on 2012-01-10
Hi,
I have recently moved our website from one 1&1 server to a higher spec 1&1 server. All seems good, but operations such as mv, cp and rm do take longer than I am used to seeing, and they do have a very noticable effect on the speed of the website. How do I fix this problem?
 
All help very much appriciated
 
many thanks
 
Mark

---

### Post by galvatron408 on 2012-01-10
you could run iostat while you're performing your command to see if there is anything out of the ordinary. You could also run strace if io seems to be ok. strace will tell you a lot of details.

I had a problem when we migrated from old hardware to new hardware and ls was hanging. I called Redhat support and they gave me the dumbest answer because they didn't want to deal with it. After half an hour on with Redhat support, I came to the realization that I wasn't going to get anywhere. I ran strace and boom, found out it was hanging on ldap. it turns out that during the move, someone had made some changes. I "undid" the change and it all started running spiffy again.

---

### Post by Lars Noodén on 2012-01-11
mv, cp and rm all rely on interaction with the file system which is on a hard disk somewhere.  Your VPS is probably just a virtual machine sharing the same hardware with dozens of other virtual machines.  As long as your activities stay in RAM they are fast but the moment you have to compete with the other VMs for hardware, things slow way down.  Just my guess.

---

### Post by marjenni on 2012-01-11
Hi,
   It is not a VPS, it is a dedicated server with 16GB ram and a 6 core processor so I am puzzled as to why deleting a deleting a directory can make the website grind.

---

### Post by gsgleason on 2012-01-11
RAM and CPU aren't going to help read/write to a slow disk.

---

### Post by marjenni on 2012-01-11
Hi,
   I was just clarifying that it is not a virtual server.

many thanks

mark

---

### Post by galvatron408 on 2012-01-13
So, have you checked iostat and strace?

> **marjenni said:**
> Hi,
   I was just clarifying that it is not a virtual server.

many thanks

mark

---

### Post by dcstar on 2012-01-16
> **marjenni said:**
> Hi,
I have recently moved our website from one **1&1** server to a higher spec 1&1 server.
........

[LIST=1]
[*]What is a "1&1" server.
[*]What Ubuntu version?
[/LIST]

---

### Post by jsra on 2012-01-16
Hi,
run dd test, eg.
```
dd if=/dev/zero of=test.file bs=64k count=16k conv=fdatasync;rm -f test.file
```
If its really low check hdd cables.

---

### Post by Lars Noodén on 2012-01-16
> **dcstar said:**
> [LIST=1]
[*]What is a "1&1" server.
[/LIST]

1&1 is a brand of hosting ("cloud") and a DNS registrar.  There are a lot of others, most of which had campaigns with discounts in response to GoDaddy's recent mistake.  You'll have to look up the discount codes:

+ [http://internet.bs/](http://internet.bs/)
+ [http://www.domainsite.com/](http://www.domainsite.com/)
+ [http://www.dynadot.com/](http://www.dynadot.com/)
+ [http://www.namecheap.com/](http://www.namecheap.com/) 
+ [http://www.hostgator.com/](http://www.hostgator.com/) 
+ [http://dreamhost.com/](http://dreamhost.com/) 
+ [http://gandi.net/](http://gandi.net/)
+ [https://dnsimple.com/goodbye-godaddy](https://dnsimple.com/goodbye-godaddy)
+ [http://www.networksolutions.com/](http://www.networksolutions.com/)

If you can, it is by far best to have the DNS registrar for your service to be different than your hosting service.  To do otherwise leave you unable to move in case of a dispute.

---

### Post by marjenni on 2012-01-19
We have two servers provided by 1&1.

Server1: Ubuntu 8.04.4
Server2: Ubuntu 10.04.2 

On Server1, cp, rm are so fast they are just instant even on very large directories.
On Server2 cp, rm on directories of similar sizes to those on server1 take serveral minutes to complete.

Server2 appears to be a much higher spec machine, and I don't understand why copies and deletes take so long. Any thoughts?

---

### Post by marjenni on 2012-01-19
Here are the results, now I have to understand them.

Linux 2.6.32-32-server  01/19/2012     _x86_64_    (6 CPU)

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           1.55    0.00    0.38    1.10    0.00   96.96

Device:            tps   Blk_read/s   Blk_wrtn/s   Blk_read   Blk_wrtn
sda              24.71      1239.48       169.58 5854583240  801018242
sdb              24.71      1239.44       169.58 5854365499  800983186
md1               0.14         0.08         1.10     395162    5179368
md3              14.83         0.66       159.23    3111809  752119906
dm-0              2.62         0.09        98.23     416036  463965377
dm-1              2.38         0.21        32.82     995042  155009433
dm-2              1.60         0.36        28.19    1678771  133145000

---

### Post by marjenni on 2012-03-21
I discovered that our original server was using hardware raid, and our new server uses software raid. I thought that this may be an obvious reason for the slowness experienced on the new server, but several people have said that it shouldn't make that much of a difference.
 
I tried copying a 1GB directory, and it took several minutes. Whilst doing this I ran iostat, a sample of the output is here:
 
Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               0.00    59.60    0.20  163.40     1.60 21633.20   132.24     4.47   27.35   5.12  83.80
sdb               0.00    58.40    0.00  164.40     0.00 21633.20   131.59     3.64   22.15   4.34  71.40
md1               0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00
md3               0.00     0.00    0.20  222.80     1.60 21633.20    97.02     0.00    0.00   0.00   0.00
dm-0              0.00     0.00    0.20   51.60     1.60  7632.40   147.37     9.24  178.34  19.19  99.40
dm-1              0.00     0.00    0.00    7.80     0.00   108.00    13.85     0.38   49.23   7.44   5.80
dm-2              0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00
Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               0.00   390.40    0.20  100.20     3.20 67190.60   669.26    42.66  423.78   9.58  96.20
sdb               0.00   390.00    0.00   99.40     0.00 66422.60   668.24    41.97  416.48   9.34  92.80
md1               0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00
md3               0.00     0.00    0.20  490.40     3.20 67264.20   137.11     0.00    0.00   0.00   0.00
dm-0              0.00     0.00    0.20  908.00     3.20 127206.60   140.07   434.08  475.53   1.10 100.00
dm-1              0.00     0.00    0.00    7.20     0.00    86.60    12.03     7.38 1024.44  41.11  29.60
dm-2              0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00
Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               0.00   347.60    0.00   83.60     0.00 57092.80   682.93    12.70  153.11   9.07  75.80
sdb               0.00   347.80    0.00   84.60     0.00 57860.80   683.93    13.87  170.71  10.57  89.40
md1               0.00     0.00    0.00    0.20     0.00     1.60     8.00     0.00    0.00   0.00   0.00
md3               0.00     0.00    0.00  430.80     0.00 57014.40   132.35     0.00    0.00   0.00   0.00
dm-0              0.00     0.00    0.20   53.60     1.60  9567.80   177.87   117.03 2216.02  18.59 100.00
dm-1              0.00     0.00    0.00    2.40     0.00    27.20    11.33     0.72  300.00  25.00   6.00
dm-2              0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00
Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               0.00   283.00    0.20  150.40     1.60 32008.20   212.55    18.87  125.37   5.70  85.80
sdb               0.00   283.40    0.20  149.60     1.60 32008.20   213.68    13.30   88.72   4.97  74.40
md1               0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00
md3               0.00     0.00    0.40  433.60     3.20 32008.20    73.76     0.00    0.00   0.00   0.00
dm-0              0.00     0.00    0.20  283.80     1.60 19240.40    67.75   299.41 1054.29   3.51  99.80
dm-1              0.00     0.00    0.00    7.80     0.00    84.80    10.87     0.36   45.64  45.64  35.60
dm-2              0.00     0.00    0.00    0.40     0.00     3.00     7.50     0.02   60.00  60.00   2.40

 
Our website ground to a halt whilst doing the copy, and dm-0 seems to be at 100% whilst doing the copy. 
 
Why would this be? Is there anything we can do to improve the situation?
 
Many thanks
 
Mark

---

### Post by dcstar on 2012-03-22
> **marjenni said:**
> 
.........
Our website ground to a halt whilst doing the copy, and dm-0 seems to be at 100% whilst doing the copy. 
 
Why would this be? Is there anything we can do to improve the situation?


I would bet good money that this will make a difference on a 10.04 system:

[http://www.webupd8.org/2010/11/alternative-to-200-lines-kernel-patch.html](http://www.webupd8.org/2010/11/alternative-to-200-lines-kernel-patch.html)

---

### Post by marjenni on 2012-03-22
Thank you for that :) unfortunately I don't think I can use this method because my top priority is keeping the server running, I can't experiment if there is any risk, and I don't want to reboot the server.

---

### Post by marjenni on 2012-03-22
Why is dm-0 maxed out when doing the file copy? 
 
many thanks
 
Mark

---

### Post by galvatron408 on 2012-03-22
that means your hardware is die-ing... 

either check your RAID configuration to see if you made a mistake or spend some money to get faster disks.

---

### Post by marjenni on 2012-03-26
I have not touched the RAID config since purchasing the server. Any idea what I should be looking for?

best regards

Mark

---

### Post by dcstar on 2012-03-27
> **marjenni said:**
> Thank you for that :) unfortunately I don't think I can use this method because my top priority is keeping the server running, I can't experiment if there is any risk, and I don't want to reboot the server.

So you apparently want a miracle solution without doing anything that might actually fix it?

Good luck.

---

### Post by marjenni on 2012-03-27
Well, I did think a miracle solution was unlikely, but unless you ask...
 
Many thanks for all of your help :)

---

