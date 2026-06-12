---
title: "Cannot continue to boot Ubuntu 64 bit Linux due to FSCK error in superblock"
date: 2011-01-07
forum: General Help
---

### Post by albertwt on 2011-01-07
Hi All,

Today for strange reason, one of my Ubuntu 64 bit server Linux VM failed to start ?
it stopped in the FSCK scan status with the error as attached.

few days back I've added new hard disk successfully and format it as sdb5 without problem.

Any guidance and comments will be highly appreciated.

Thanks.

---

### Post by McNils on 2011-01-07
Boot the machine from CD/USB and run fsck from that system. It might help.

---

### Post by albertwt on 2011-01-07
> **McNils said:**
> Boot the machine from CD/USB and run fsck from that system. It might help.

thanks for the suggestion, I'll try that. At the moment I couldn't copy paste the /etc/fstab content here because the boot process was stuck as in the screenshot.

---

### Post by albertwt on 2011-01-08
> **McNils said:**
> Boot the machine from CD/USB and run fsck from that system. It might help.

Thanks for your response mate, however I've made changes to the **/etc/fstab** from 2 into all 0 then it boot up normally.
so can I conclude that since this Linux is running as Virtual Machine, therefore I do not need to perform any FSCK (for all Linux VM make the FSCK level into 0).

is that correct or can be applied to all of my production VM ?

---

