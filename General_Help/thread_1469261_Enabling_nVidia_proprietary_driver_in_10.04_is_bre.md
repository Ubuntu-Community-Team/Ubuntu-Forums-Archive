---
title: "Enabling nVidia proprietary driver in 10.04 is breaking Ubuntu."
date: 2010-05-02
forum: General Help
---

### Post by JaLaRu on 2010-05-02
Hi, I'm having a problem with the newest Ubuntu...

Everything works great at the moment, no hardware problems or anything like that. But whenever I enable the proprietary nVidia driver 185, it causes the boot screen to not come up, Ubuntu stops recognising my sound-card and refuses to work and when I try to shut down or restart, it just takes me back to the log in screen. When I remove the driver, everything works okay again.

I've not had this problem in Ubuntu 9.10 or in the 1st and 2nd beta of 10.04.

Can anyone help?

---

### Post by swappa on 2010-05-02
Sure about the driver version?
I am using 195.36.15 and it is working perfectly. 
Maybe you could try this version?

---

### Post by JaLaRu on 2010-05-02
> **swappa said:**
> Sure about the driver version?
I am using 195.36.15 and it is working perfectly. 
Maybe you could try this version?

Sorry, I meant the latest version in jockey. I'm just used to it being 185 for some reason.

I can get 173 to work without the problems I was having with the latest version, there is just an ugly low resolution boot screen. But I think I should probably try to get the newest driver working for better performance.

Also, I forgot to say, my card is a nVidia 9200.

---

### Post by Xgen on 2010-05-02
Although I had many problems with nvidia through the lucid development stage, it seems stable now. I'm using the nvidia 173.14.25 propriety driver with the 2.6.34rc6 kernel. Plymouth works fine (for the 4 seconds that it appears). The only additional thing that I did was blacklist nouveau and vga16fb in modprobe.d...but that might not have been necessary. No problems with the boot menu either.

---

