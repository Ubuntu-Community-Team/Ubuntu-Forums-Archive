---
title: "Can't install vmWare Tools in Kubuntu LucidLynx"
date: 2010-07-25
forum: General Help
---

### Post by kumaraSrlk on 2010-07-25
Hi,

I installed Kubuntu LucidLynx(10.04) on vmWare workstation 6.5 and I can't install vmWare tools on it. I ran the vmWare tools installer and it says that it needs the path of kernel header files and it suggests "/usr/src/linux/include" to be the path. But, there is no such path on my file system. I tried to find the path by using kfind and all the results point to some empty folders.

Doesn't kubuntu provide those files by default? 

I tried to find the kernel version and found it's "2.6.32-21.32 [kernel]("http://kernel.org/") based  on 2.6.32.11" ([https://wiki.ubuntu.com/LucidLynx/TechnicalOverview#Linux%20kernel%202.6.32](https://wiki.ubuntu.com/LucidLynx/TechnicalOverview#Linux%20kernel%202.6.32))

Should I download the kernel source from kernel.org and copy the include folder to "/usr/src/linux/include" ? If I should, which version, 2.6.32-21.32 or 2.6.32.11 ?

Or is there any way to get the header files by apt ? If so, where should I put those files to?

BTW, when u download something using apt, where are those files saved to?

Thanks a lot.

---

### Post by dcstar on 2010-07-25
> **kumaraSrlk said:**
> Hi,

I installed Kubuntu LucidLynx(10.04) on vmWare workstation 6.5 and I can't install vmWare tools on it. I ran the vmWare tools installer and it says that it needs the path of kernel header files and it suggests "/usr/src/linux/include" to be the path. But, there is no such path on my file system. I tried to find the path by using kfind and all the results point to some empty folders.

Doesn't kubuntu provide those files by default? 

I tried to find the kernel version and found it's "2.6.32-21.32 [kernel]("http://kernel.org/") based  on 2.6.32.11" ([https://wiki.ubuntu.com/LucidLynx/TechnicalOverview#Linux%20kernel%202.6.32](https://wiki.ubuntu.com/LucidLynx/TechnicalOverview#Linux%20kernel%202.6.32))

Should I download the kernel source from kernel.org and copy the include folder to "/usr/src/linux/include" ? If I should, which version, 2.6.32-21.32 or 2.6.32.11 ?

Or is there any way to get the header files by apt ? If so, where should I put those files to?

BTW, when u download something using apt, where are those files saved to?

Thanks a lot.

Look in the Virtualization forum for all VM issues, this is already answered in the posts at the top.

---

