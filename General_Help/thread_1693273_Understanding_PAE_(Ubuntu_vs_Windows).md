---
title: "Understanding PAE (Ubuntu vs Windows)"
date: 2011-02-22
forum: General Help
---

### Post by spliffeh on 2011-02-22
I'm trying to understand PAE a bit better, specifically the differences between PAE on Windows and PAE on Ubuntu. The deeper I read into this the more of a headache it's giving me. 

Note **_[this post]("http://forums.laptopvideo2go.com/topic/17165-4gb-ram-limit-in-32bit-os-pae-dep-4gt/page__st__20__p__89122#entry89122")_** (the entire thread is good - but reply #24 which I've linked nails it on the head)

So from what I understand so far: PAE on Windows was purposely crippled by Microsoft because it caused a lot of instability/crashes due to drivers/apps not written properly to handle anything other then 32bit.  PAE is currently implemented by default on 32bit Windows 7 (if your hardware supports it). However you will still only see ~3gb of ram available from task manager. PAE is crippled only used for DEP (and I'm still not sure what the advantage of this is if it doesn't free up more memory - if anyone could explain I'd appreciate it). 

**The question:** does PAE on Ubuntu 32bit work the same? I'm told with Ubuntu PAE I will see 4GB available. But is it really usable or is it just reporting the total memory (not the usuable memory) Does Ubuntu 32bit PAE cause instability like Microsoft encountered? Is it a crippled version like Windows or are Ubuntu 32bit drivers/apps more PAE friendly?

Thanks in advance

---

### Post by TenPlus1 on 2011-02-22
The PAE Kernel in Ubuntu will SEE and USE all of your memory and work perfectly although not as fast as a true 64-bit processor and kernel would work...

---

### Post by spliffeh on 2011-02-22
> **TenPlus1 said:**
> The PAE Kernel in Ubuntu will SEE and USE all of your memory and work perfectly although not as fast as a true 64-bit processor and kernel would work...

I'd like to understand how Ubuntu's PAE is able to do this VS Windows7's PAE which is not. 

Are the Ubuntu drivers/apps writen to be more "PAE aware" or something? Or is there the same potential for instability as there would be with "uncrippled" PAE on Windows?

---

