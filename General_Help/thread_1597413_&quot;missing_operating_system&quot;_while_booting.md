---
title: "&quot;missing operating system&quot; while booting from USB"
date: 2010-10-15
forum: General Help
---

### Post by ildella on 2010-10-15
Hi. I used to follow a procedure that worked to burn a live system on a USB. 
I create a "dist" with remastersys. 
I create two ext3 partition: first with no label, second with label "casper-rw". 

Then I burned the iso created by remastersys on the first partition and I get the live.

Somewhere in last month, something got broken and every USB drive I create, can't boot and I get the "missing operating system" message on every computer I try. 

What should I investigate? I think UNetBootin is working cause it can burn a ISO downloaded from Ubuntu web site. So maybe remastersys, but I do not know where to start investigating. Any help?

---

### Post by C.S.Cameron on 2010-10-15
Ext3 is ok for casper-rw but a Live filesystem should go on FAT3. (I think).

---

