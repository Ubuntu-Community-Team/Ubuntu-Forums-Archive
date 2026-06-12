---
title: "Defragging and swap space questions"
date: 2012-01-24
forum: General Help
---

### Post by coldjeanz on 2012-01-24
First, what exactly is swap space? I read this in the FAQ

> The following will increase your swap to 2 GB. Replace count= with the number of kilobytes you want for your swap file.

sudo su
swapoff -a
cd /host/ubuntu/disks/
mv swap.disk swap.disk.bak
dd if=/dev/zero of=swap.disk bs=1024 count=2097152
mkswap swap.disk
swapon -a
free -m

My system monitor says I have 0 bytes of 256 MiB Swap. What does that mean and is it beneficial to add more?

Another question I have is if it's necessary to defrag when using Ubuntu through wubi? Will it help disc performance any, and which program should I use if so?

thanks

---

### Post by wolfen69 on 2012-01-24
> **coldjeanz said:**
> First, what exactly is swap space? 
It is used like virtual memory in windows. Swap is on your hard drive, and is used in case you run low on physical memory.

> My system monitor says I have 0 bytes of 256 MiB Swap. What does that mean and is it beneficial to add more?
It would depend. How much RAM do you have? Is it a laptop? Are you going to use hibernate?

> Another question I have is if it's necessary to defrag when using Ubuntu through wubi? 

Generally, there is no need to defrag in linux. Files are handled differently than in windows.

Wubi is *OK* to try ubuntu, but if you like using ubuntu, consider doing a proper dual boot eventually. Performance will be a bit better. Wubi is not looked highly upon around here.

---

### Post by coldjeanz on 2012-01-24
I'm still using Wubi because I can access all my Windows file through the host folder which is really nice. I don't think I would be able to do that with a real dual boot would I?

Oh yeah I have 3.7 GB of RAM available and yes it's a laptop

---

### Post by xyzzyman on 2012-01-24
System Monitor is telling you that you aren't using any of your 256MB's of swap. I have a 4.25GB swap partition as I have 4GB's of RAM and I never use any of it. Always says 0 of 4.25GB. I keep it though so I can hibernate, which I never seem to actually do. lol

---

### Post by Frogs Hair on 2012-01-24
256 MB is the default swap for a Wubi installation and the 0 means no swap is in use . You can sleep / suspend with a Wubi installation ,  but hibernation is not possible with that amount of swap . It is possible to increase the amount swap , but I don't know if this will allow hibernation in a Wubi installation .

Windows defrag will not be able to process anything inside  the Ubuntu  partition / folder . Remember that Wubi is for trial / temporary use . If you find you like Ubuntu it may be worth  installing a traditional dual boot .

Wubi can be moved to a partition or the 30 GB max disk space can be increased but , these operations can be complicated  compared to  a dual boot . There is also the possibility that both operating systems get broken .

---

### Post by oldos2er on 2012-01-24
> **coldjeanz said:**
> I'm still using Wubi because I can access all my Windows file through the host folder which is really nice. I don't think I would be able to do that with a real dual boot would I?


Ubuntu can read and write to NTFS partitions just fine.

---

### Post by alphaamanitin on 2012-01-24
> **oldos2er said:**
> Ubuntu can read and write to NTFS partitions just fine.


I see a lot of people on here saying not to write to NTFS.  Personally, I dual boot a laptop from an external HD with Ubuntu on it, and Windows 7 on the internal drive.  I never have an issue reading/writing to my NTFS drive, but a lot of people seem to think it is an issue, is it?

AlphaA

---

### Post by wolfen69 on 2012-01-25
> **alphaamanitin said:**
> I never have an issue reading/writing to my NTFS drive, but a lot of people seem to think it is an issue, is it?



I've been writing to my ntfs drives for years with no issues. I can't speak for other people's experiences, but as far as I know, it is safe.

---

