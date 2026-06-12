---
title: "speed up ubuntu on a netbook"
date: 2009-09-12
forum: General Help
---

### Post by perrabyte on 2009-09-12
Made a regular install of Ubuntu 9.04 on a fast (write speed of 20MB/s) SDHC card on a netbook. I was amazed that it worked without any changes, just point and click.

Was wondering if it is possible to utilize the Linux Software Raid to make a Raid0 of two partitions on two separate SDHC cards. The reason for this is because it would further boost netbook performance, I hope.

There are now readily available SDHC cards up to 32GB with transfer speeds up to 30MB/s but I saw in the wiki that there will be SDXC cards up to 2TB running from 100 to 300MB/s. With this in mind I think it would be the easiest way to speed up your computer running ubuntu together with a slow HDD running windows.

Anyone who can help me testing raid0?

---

### Post by Bucky Ball on 2009-09-12
Have you also thought about Ubuntu Netbook Remix?

---

### Post by hibliss on 2009-09-12
That write speed is still abysmal compared to the spinning hard drive, or SSD that comes with it. You are better off with a regular install on the hard drive if speed is your goal.

---

### Post by perrabyte on 2009-09-12
> **hibliss said:**
> That write speed is still abysmal compared to the spinning hard drive, or SSD that comes with it. You are better off with a regular install on the hard drive if speed is your goal.

Its not always the case, my SSD ( asus eee 900 ) is pretty slow  and if the user wants to keep windows wubi doesnt cut it.

---

### Post by rob-ward on 2009-09-12
If you want raid0 then you need to install from the alternate CD, should be no problem with using 2 sd cards although I have never done that, when installing you will have to set the partitions on the SD cards as raid partitions and then select the create raid option, there you can designate which partitions to use and what raid mode you want.

---

### Post by perrabyte on 2009-09-12
Thanks, I will try.

---

### Post by rob-ward on 2009-09-12
k, once you have had ago if you could would you post your results here and any problems/difficulties you had as I think I might give this a try on one of my computers if it works.

---

### Post by P4man on 2009-09-12
> **perrabyte said:**
> 
Was wondering if it is possible to utilize the Linux Software Raid to make a Raid0 of two partitions on two separate SDHC cards. The reason for this is because it would further boost netbook performance, I hope.


Ive never done a software raid, but I see no reason it wouldn't work. And its a cool idea, so go for it and let us know :).

However, one big caveat.. Already SD cards aren't known for great reliability, especially when doing lots of writes, so putting 2 in raid means if either of them develops problems, you'll face enormous problems trying to retrieve anything. Basically, it will be impossible, Make backups often!

---

### Post by perrabyte on 2009-09-17
Have now tested the raid0 configuration using a separate ext3 partition for /boot using the alternate ubuntu 9.04 CD. There wasn't really any performance boost over a single SDHC card for the typical disc load.:( Therefore I'm going to wait for cheaper and better cards to install on instead.

---

### Post by Bucky Ball on 2009-09-17
One thing people continually choose to forget is that SSD wears out much quicker than a hard drive ... think about it ...

Any kind of Flash device can only be written to so many times and before you know it ... your netbook is landfill. 


Think about our future ...

---

### Post by perrabyte on 2009-09-17
> **Bucky Ball said:**
> One thing people continually choose to forget is that SSD wears out much quicker than a hard drive ... think about it ...

Any kind of Flash device can only be written to so many times and before you know it ... your netbook is landfill. 


Think about our future ...

Nah, guarantee of 10 years normal use. I think I will have had my install upgraded long before it breaks down. HDD have mechanical parts that are much more prone to failure.

---

### Post by winotree on 2009-09-17
> **Bucky Ball said:**
> One thing people continually choose to forget is that SSD wears out much quicker than a hard drive ... think about it ...

Any kind of Flash device can only be written to so many times and before you know it ... your netbook is landfill. 


Think about our future ...

The only device I know is the one I use on a daily basis, and your point was argued up one side and down the other a few years back at *EeeUser*.  This article [http://wiki.eeeuser.com/ssd_write_limit](http://wiki.eeeuser.com/ssd_write_limit) is from their wiki and I'm sure we'll all agree twenty-five years is an acceptable lifespan for an SSD, landfills not withstanding.  :D  ;)

---

