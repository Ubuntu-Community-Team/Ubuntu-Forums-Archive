---
title: "How to migrate to a bigger hard drive"
date: 2011-10-22
forum: General Help
---

### Post by yilin on 2011-10-22
I have win2k, winxp and ubuntu on a 120G hard drive with Latitude D630. I used bootpart for the multi-booting.

I'd like to migrate the whole thing into a 500Gb hard drive, hoping avoid the whole installation, configuration, updating nightmare... 

Is that all possible? What software can help me with this?

Thanks a lot!

---

### Post by haqking on 2011-10-22
> **yilin said:**
> I have win2k, winxp and ubuntu on a 120G hard drive with Latitude D630. I used bootpart for the multi-booting.

I'd like to migrate the whole thing into a 500Gb hard drive, hoping avoid the whole installation, configuration, updating nightmare... 

Is that all possible? What software can help me with this?

Thanks a lot!

[www.clonezilla.org](www.clonezilla.org)

---

### Post by dcstar on 2011-10-22
> **yilin said:**
> I have win2k, winxp and ubuntu on a 120G hard drive with Latitude D630. I used bootpart for the multi-booting.

I'd like to migrate the whole thing into a 500Gb hard drive, hoping avoid the whole installation, configuration, updating nightmare... 

Is that all possible? What software can help me with this?

Thanks a lot!

An Ubuntu Live CD/USB and **gparted** will do it, or the other tool in the previous post.

---

### Post by haqking on 2011-10-22
> **dcstar said:**
> An Ubuntu Live CD/USB and **gparted** will do it, or the other tool in the previous post.

gparted will setup partitions, but it wont migrate his existing installation to that new hard drive avoiding installation etc 

or am i reading your post wrong ?

---

### Post by masgeeks on 2011-10-22
clonezilla works great but takes forever to clone a large HD - so, plan your time accordingly...!!!

---

### Post by enkay009 on 2011-10-22
Ubuntu should be easy enough to migrate. Like everyone else already said: gparted or clonezilla. 

However Windows might be a challenge. If I remember correctly, Windows XP has a security feature that prevents you from changing your CPU or moving the OS to another drive. Whatever you do, make sure you can rollback.

---

### Post by masgeeks on 2011-10-22
Windows does get cranky, but *usually* you can reactivate it.  I just moved a Server 2008 VM from one Ubuntu machine to another - different hardware on both, and was prompted to reactivate Windows, which I did, and it didn't give me grief - and this was the third time I have moved the VM between different machines.  Might not be so simple moving XP to a different hard drive, though?  I know I can swap XP VM's around all over the place without any issues, lol...  There is a nifty utility from VMware I have used, which will allow you to turn your Windows install into a virtual disk... so you can run it elsewhere as a virtual machine.  That worked well for me and I was able to run it in Virtualbox on Ubuntu (which will allow you to add a virtual disk that is in VMware format)... it prompted me to reactivate as well - but it did not give me any hassle.  It reactivated.  As stated, make sure you have an escape plan before you do anything...  :)

---

### Post by haqking on 2011-10-23
> **masgeeks said:**
> clonezilla works great but takes forever to clone a large HD - so, plan your time accordingly...!!!

my 200 GB HDD (not big i know) takes about 10 minutes with restoration checking, but i guess it is all relative to the user experience and hardware

---

