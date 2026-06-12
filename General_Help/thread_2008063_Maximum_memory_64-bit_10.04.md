---
title: "Maximum memory 64-bit 10.04"
date: 2012-06-22
forum: General Help
---

### Post by hroitblat on 2012-06-22
We now have servers that have a large amount of memory.  How much memory can Ubuntu 10.04 access?  Can it access all 96 GB?

We're still using 10.04, but we could conceivably upgrade to a later version if necessary.

I know that in theory, a 64 bit OS should be able to access more than a TB, what can our system do in practice?

Thanks.
Herb

---

### Post by sanderj on 2012-06-22
Did you Google it? [https://help.ubuntu.com/community/32bit_and_64bit#Memory](https://help.ubuntu.com/community/32bit_and_64bit#Memory)

"A 64-bit computer will be able to address up to 16.8 million TB (16 exabytes) although constraints are in place that limit this to around 1TB."

---

### Post by hroitblat on 2012-06-22
Thanks, yes, I read that.  However, I find that rather vague.  Do you have any experience with using a large amount of memory?  In theory it should work with a TB, but does it actually?

---

### Post by Lee_Bo on 2012-06-22
12.04 will see 32 gb's of memory.  Unfortunately that's all I have left available to use on my VMware server.

---

### Post by Gyokuro on 2012-06-22
Hi,

your 96GB are not a problem, below an output of a machine with 128GB

free -g

             total        used       free     shared    buffers     cached 
Mem:           125             60              65                 0                       0              35
 -/+ buffers/cache:         25        100
 Swap:           30          0         30

bare metal is: **HP Proliant DL180 G6**

---

### Post by Old_Grey_Wolf on 2012-06-22
> **Gyokuro said:**
> 
your 96GB are not a problem, ...
... bare metal is: **HP Proliant DL180 G6**

Same here using HP Proliant DL360 with 192GB.

---

