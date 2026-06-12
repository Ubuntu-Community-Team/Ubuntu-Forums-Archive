---
title: "mount -a  does not like my -b size"
date: 2009-08-21
forum: General Help
---

### Post by supremedalek on 2009-08-21
I have here a partition I formatted as xfs. The rest of the system is ext3. I had to reformat the said partition. So, I umounted it, reformatted it using 

```
mkfs.xfs -f -d sunit=128,swidth=384 -b size=64k /dev/mapper/vbox-vms

```

and tried to mount it using mount -a as it was defined in my fstab:

```
% sudo mount -a
mount: Function not implemented
%
```

Fine, I then tried to manually mount it. Got the same error message. If I remove the -b size=64k from my mkfs statement, mount works fine. Clearly it does not like my -b size statement. Trying size=16k also gives the same results. Is there a way around that? BTW, this is a X86_64 install of jaunty,

```
% uname -a
Linux vbox 2.6.28-15-server #48-Ubuntu SMP Wed Jul 29 09:38:22 UTC 2009 x86_64 GNU/Linux
%
```

---

### Post by dcstar on 2009-08-21
> **supremedalek said:**
> I have here a partition I formatted as xfs. The rest of the system is ext3. I had to reformat the said partition. So, I umounted it, reformatted it using 

```
mkfs.xfs -f -d sunit=128,swidth=384 -b size=64k /dev/mapper/vbox-vms

```
..........
Fine, I then tried to manually mount it. Got the same error message. If I remove the -b size=64k from my mkfs statement, mount works fine. Clearly it does not like my -b size statement. Trying size=16k also gives the same results. Is there a way around that? BTW, this is a X86_64 install of jaunty,


You do not "mount" things with blocksizes, blocksizes are used in creating the partition and mount must use whatever is there.

---

