---
title: "No option for install side by side"
date: 2010-11-16
forum: General Help
---

### Post by Ledus on 2010-11-16
When trying to install Ubuntu 10.10(32bit) for my laptop i get no option to install side by side with another OS.

I believe that i'll have to use G-partitioner(?) or something like that however i do not know how that works.

Also the first time that i tried to install ubuntu on my laptop i got the option for installing it side by side however i quit and "tried" ubuntu to see if it was compataible with my hardware. 

Also another question...

Would it be a better option to install 10.4 (LTS) rather than 10.10?

---

### Post by Ledus on 2010-11-16
bump

---

### Post by geoffmcc on 2010-11-16
I currently use 10.10 and have a small Windows partition.

I installed Win7 First and kept the drive as just one 600 gig (in my case) partition. I then booted 10.10 and selected the install option. Went threw next and when get to the first partition question, the first one is and is selected "Install along side". From there you just next and there is a slide bar where you just slide to adjust the size of the Ubuntu partition.

So, if your not getting the "Along side" option and you have one hard drive with a partition created in windows for ubuntu - merge it back into c: and then reboot and try to install again.

Hope that helps


Edit: I didn't notice the last thing you said before, that you had the option and then restarted. But I would say boot windows and check the partitions

---

### Post by Ledus on 2010-11-16
> **geoffmcc said:**
> I currently use 10.10 and have a small Windows partition.

I installed Win7 First and kept the drive as just one 600 gig (in my case) partition. I then booted 10.10 and selected the install option. Went threw next and when get to the first partition question, the first one is and is selected "Install along side". From there you just next and there is a slide bar where you just slide to adjust the size of the Ubuntu partition.

So, if your not getting the "Along side" option and you have one hard drive with a partition created in windows for ubuntu - merge it back into c: and then reboot and try to install again.

Hope that helps


Edit: I didn't notice the last thing you said before, that you had the option and then restarted. But I would say boot windows and check the partitions

Windows didnt find anything however g-parter on ubuntu(when you are "trying" it) finds a 3mb unallocated space

---

### Post by geoffmcc on 2010-11-16
> **Ledus said:**
> Windows didnt find anything however g-parter on ubuntu(when you are "trying" it) finds a 3mb unallocated space

I believe that is grub

---

### Post by oldfred on 2010-11-16
See the issues listed in the first link.

Some examples of installs and issues:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://www.dedoimedo.com/computers/ubuntu-maverick.html](http://www.dedoimedo.com/computers/ubuntu-maverick.html)


I prefer to use gparted to create partitions in advance, then use manual install to format & select partitions for / (root) and (if separate partition) /home. If created in advance it finds existing swap partition.

---

### Post by wojox on 2010-11-16
> **Ledus said:**
> 
Would it be a better option to install 10.4 (LTS) rather than 10.10?

Yes. :P

---

