---
title: "Shell scripting Help"
date: 2012-02-17
forum: General Help
---

### Post by Vishal Agarwal on 2012-02-17
Hi,
i wanted to filter out  "DPT=25" from the following log report from iptables.

Feb 17 14:20:25 mail2 kernel: [  864.623534]  IPTBL SMTP OPT IN= OUT=eth1 SRC=xxx.xxx.xxx.xxx DST=xxx.xxx.xxx.xxx LEN=40 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=TCP SPT=53835 **DPT=25** WINDOW=0 RES=0x00 RST URGP=0

But when I filter  **grep /path/to/file "DPT=25"** it filters out also "*DPT=2549*"; which is not required.

Thanks in advance.

---

### Post by lncoll on 2012-02-17
Have you tried ?
```

grep /path/to/file "DPT=25 "

```

---

### Post by Vishal Agarwal on 2012-02-17
Thanks a Lot.
> 
fgrep /path/to/file "DPT=25 " 


It worked.

---

### Post by Khayyam on 2012-02-17
> **Vishal Agarwal said:**
> ```
fgrep /path/to/file "DPT=25 "
```

For very large logs it is more optimal to use awk and stipulate the field, this means it only checks the field for the value of field and not the whole file.

```
awk '$23=="DPT=25"' /path/to/file
```

Also we don't have to stipulate a space as its a field value not a string match.

HTH ... khay

---

### Post by Vishal Agarwal on 2012-03-04
> **Khayyam said:**
> For very large logs it is more optimal to use awk and stipulate the field, this means it only checks the field for the value of field and not the whole file.

```
awk '$23=="DPT=25"' /path/to/file
```Also we don't have to stipulate a space as its a field value not a string match.

HTH ... khay


Great use of awk. it's so fast and can handle 7GB log file very quickly. Thanks Again

---

### Post by Khayyam on 2012-03-04
> **Vishal Agarwal said:**
> Great use of awk. it's so fast and can handle 7GB log file very quickly. Thanks Again

Your welcome ... but if you have a 7GB iptables log then I need to mention one word: 'logrotate'. You can break these logs down by month, week, or something more manageable than 7GB. Plus smaller logs can be backed up to CD easily, and so free up some space on the host machine.

I'm trying to mentally calculate how many lines a 7GB files would have, but no. That one line above is 209bytes, so 7,516,192,768 / 209 that is 35,962,645 ... nearly 36 million lines. How long did awk take to parse it? Actually, if you run the command again can you post the output of 'time' and the exact size of the log? 

```
time awk '$23=="DPT=25"' logfile
```best ... khay

---

### Post by Vishal Agarwal on 2012-03-13
> **Khayyam said:**
> Your welcome ... but if you have a 7GB iptables log then I need to mention one word: 'logrotate'. You can break these logs down by month, week, or something more manageable than 7GB. Plus smaller logs can be backed up to CD easily, and so free up some space on the host machine.

I'm trying to mentally calculate how many lines a 7GB files would have, but no. That one line above is 209bytes, so 7,516,192,768 / 209 that is 35,962,645 ... nearly 36 million lines. How long did awk take to parse it? Actually, if you run the command again can you post the output of 'time' and the exact size of the log? 

```
time awk '$23=="DPT=25"' logfile
```best ... khay

I did it knowingly 7GB. for testing purpose. Otherwise the logrotate is already enabled.

---

