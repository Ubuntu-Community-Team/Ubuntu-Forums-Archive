---
title: "Invalid arithmetic operator. Trying to take away two numbers with decimals"
date: 2011-02-07
forum: General Help
---

### Post by Sam1994 on 2011-02-07
I'm trying to make a bash script that takes away two decimal numbers. This is to work out partitioning information.

```

hddsize=`sudo parted -s /dev/sda unit GB print | grep "Disk" | tr -d [A-Z][a-z] | tr -d '/: '`
trimsize="1.5"
partitionendsize=$(($hddsize - $trimsize))

```I get an invalid arithmetic operator. Not sure how to minus these two numbers. Is it a floating point issue?

TIA

---

### Post by sisco311 on 2011-02-07
> **Sam1994 said:**
> Is it a floating point issue?


Yes, you have to use bc, dc or awk:
[http://mywiki.wooledge.org/BashFAQ/022](http://mywiki.wooledge.org/BashFAQ/022)

---

