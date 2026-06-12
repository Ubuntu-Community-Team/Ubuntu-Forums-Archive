---
title: "Lucid not showing all RAM"
date: 2010-10-31
forum: General Help
---

### Post by Enigmapond on 2010-10-31
Hi,

I have a Dell Inspiron 1764 with 4GB of RAM. I have Win7 and Lucid as a dual boot. My processor is quad core Intel Core i5 M430 @2.27GHz. The problem is that I should show 4GB of RAM but the Ubuntu side only shows 2.9GB and the readout on conky shows 2.88GB. Why is this? Is Ubuntu not utilizing all available RAM? Your input would be most appreciated.

Thank You!

---

### Post by bobcollard on 2010-10-31
> **Enigmapond said:**
> Hi,

I have a Dell Inspiron 1764 with 4GB of RAM. I have Win7 and Lucid as a dual boot. My processor is quad core Intel Core i5 M430 @2.27GHz. The problem is that I should show 4GB of RAM but the Ubuntu side only shows 2.9GB and the readout on conky shows 2.88GB. Why is this? Is Ubuntu not utilizing all available RAM? Your input would be most appreciated.

Thank You!
Two problems are known without your information about the system.  First: the Graphics card will use some of the RAM off the top so you will never see a full 4GB.  Second: if you are using a 32 bit version of Ubuntu then it does not use all of the RAM or show it.  In some cases, like Linux Mint they use a different Kernel with PAE that shows more than 3GB using a 32 bit system.

---

### Post by davidvandoren on 2010-10-31
You have to install the PAE kernel.

---

### Post by Enigmapond on 2010-10-31
Thank you for your response....that explains a lot actually. I forgot that the graphics card will use a lot but I didn't know it wouldn't show and yes I'm currently using 32bit. The system runs great and I have the swapness set to 10 and NEVER get above 50% of the RAM..but I was just curious. Thanks Again!

> **davidvandoren said:**
> You have to install the PAE kernel.

I have no idea what that is. Do I really need it? I'd hate to start messing with kernels when I'm running very stable right now....

---

### Post by bobcollard on 2010-10-31
> **Enigmapond said:**
> Thank you for your response....that explains a lot actually. I forgot that the graphics card will use a lot but I didn't know it wouldn't show and yes I'm currently using 32bit. The system runs great and I have the swapness set to 10 and NEVER get above 50% of the RAM..but I was just curious. Thanks Again!



I have no idea what that is. Do I really need it? I'd hate to start messing with kernels when I'm running very stable right now....
You are welcome.  If this solves your question then please Edit your first post Title and add [Solved] so others will benefit from your experience.

---

### Post by Enigmapond on 2010-10-31
Just as a side note, I installed the kernel with PAE and was unable to connect via wireless. I tried to install the Broadcom driver but kept getting an error....sooooo I uninstalled the kernel. We are running very well so I see that this PAE kernel is not a necessity.

Cheers!

---

### Post by dcstar on 2010-11-01
> **Enigmapond said:**
> Just as a side note, I installed the kernel with PAE and was unable to connect via wireless. I tried to install the Broadcom driver but kept getting an error....sooooo I uninstalled the kernel. We are running very well so I see that this PAE kernel is not a necessity.

Cheers!

PAE kernels are generally server kernels, server kernels may not support items used by desktops (like Wireless hardware).

---

### Post by HiImTye on 2010-11-01
switch to 64 bit and you will see (most of) your ram (assuming that you have a 64 bit processor) otherwise you will never actually get your full amount of memory. 32 bit operating systems have a limitation of 4GB of addressing space for memory (all memory, including video, any memory used by expansion slots, like sound cards, etc). the only other way would be to switch to a PAE kernel but you already tried that

---

### Post by TNT1 on 2010-11-01
> **dcstar said:**
> PAE kernels are generally server kernels, server kernels may not support items used by desktops (like Wireless hardware).

Say what? I have been running PAE kernels on desktops for at least two years now with not a single problem.

---

