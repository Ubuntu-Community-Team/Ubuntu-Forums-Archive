---
title: "Mount errors on Boot"
date: 2006-03-26
forum: General Help
---

### Post by Adanufgail on 2006-03-26
Upon booting Ubtunu,
I get the following message
> Uncompressing Linux... OK, booting the kernel.
Loading, please wait...
mount: Mounting /dev/hdb2 on /root failed: invalid argument
mount: Mounting /root/dev on /dev/.static/dev failed: no such file or directory
mount: Mounting /dev on /root/dev failed: No such file or directory.

I believe the error comes in the first mount, but I am not able to say why it does this. For the record, here is the partitions of HDB:

HDB1: 220 GB NTFS (Works in Windows)
HDB2: 95 GB EXT3
HDB3: 5 GB Swap

It was a while after I installed Ubuntu that this problem surfaced. It was not the first, nor the first ten boots. I have been able to boot into Windows XP, and then back to Ubuntu, and back to XP before the problem. I may have installed new Ubuntu updates (including a possible update to the kernel) the last time it was run. I can list the kernels, but I am fairly sure I have tried all of them and recieve the above error. Any help in this situation would be greatly appreciated.

---

### Post by taurus on 2006-03-26
Can you post the content of /etc/fstab?
```

more /etc/fstab

```

---

### Post by Adanufgail on 2006-03-26
hmmm... this could be a problem.

/etc/fstab doesn't exist

I even cd'd to /etc and there is not fstab.
Not much of anything really.

How would I go about recreating fstab (I know it's used in booting)?

---

