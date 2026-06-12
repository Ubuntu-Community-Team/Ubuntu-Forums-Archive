---
title: "x86 - detect over 4GB in the newer ubuntu?"
date: 2011-10-28
forum: General Help
---

### Post by altjx on 2011-10-28
Forgive me if this has been asked already, but I planned to install Ubuntu 11.10 when I get home. But I couldn't remember if Ubuntu detected over 4GB the last time I installed it. I thought I installed the 32-bit of it, but I do remember seeing it detect all 8 gigs.

Is it true that the latest 32-bit Ubuntu can detect over 4 gigs? 

Thanks

---

### Post by haqking on 2011-10-28
> **altjx said:**
> Forgive me if this has been asked already, but I planned to install Ubuntu 11.10 when I get home. But I couldn't remember if Ubuntu detected over 4GB the last time I installed it. I thought I installed the 32-bit of it, but I do remember seeing it detect all 8 gigs.

Is it true that the latest 32-bit Ubuntu can detect over 4 gigs? 

Thanks

it defaults to using the PAE kernel now so yes it will see your RAM.

However if you have x64 architecture i would recommend the x64 install

---

### Post by altjx on 2011-10-28
> **haqking said:**
> it defaults to using the PAE kernel now so yes it will see your RAM.

However if you have x64 architecture i would recommend the x64 install

Gotcha. I'm able to use the 64-bit OS, but I just thought 32-bit would be better for compatibility. Do you think I'd run into many issues using the 64-bit? I have in the past, but this was prior to even Ubuntu 10.04 I believe.

---

### Post by LinuxFan999 on 2011-10-28
> **altjx said:**
> Forgive me if this has been asked already, but I planned to install Ubuntu 11.10 when I get home. But I couldn't remember if Ubuntu detected over 4GB the last time I installed it. I thought I installed the 32-bit of it, but I do remember seeing it detect all 8 gigs.

**Is it true that the latest 32-bit Ubuntu can detect over 4 gigs?** 

Thanks
Yes, but only if it installs the PAE kernel, otherwise no. If you have a 64bit processor and 4 gigabytes of RAM or more, you should install the 64bit version of Ubuntu. If you have less than 4 gigabytes of RAM, you should install the 32bit version of Ubuntu.

---

### Post by 11jmb on 2011-10-28
Compatibility issues should not be a huge concern, especially when installing from the repositories. You may have to change a few compiler flags for source installs, though

---

### Post by altjx on 2011-10-28
Gotcha. Thanks, can't wait to put this back on my desktop and laptop.

---

### Post by haqking on 2011-10-28
> **LinuxFan999 said:**
> Yes, but only if it installs the PAE kernel, otherwise no. If you have a 64bit processor and 4 gigabytes of RAM or more, you should install the 64bit version of Ubuntu. If you have less than 4 gigabytes of RAM, you should install the 32bit version of Ubuntu.

I believe the PAE is used by default now.

Also having less than 4GB does not mean you need 32 bit, you can still run x64 on less than 4GB and often people do.

---

