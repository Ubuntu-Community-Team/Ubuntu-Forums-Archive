---
title: "Install on multiple hard drives?"
date: 2011-08-21
forum: General Help
---

### Post by linuxuser12345 on 2011-08-21
I am doing a new build with an SSD / HDD combo, and I am wondering, is there a way I can install Ubuntu spread across both drives? I know I can do this in Fedora, but I haven't seen much of a feature like this in Ubuntu. Can someone help me out?

---

### Post by sanderd17 on 2011-08-21
When you install Ubuntu, you need to use the "manual method" and choose which part of Ubuntu you put on which partition.

---

### Post by linuxuser12345 on 2011-08-21
How would you suggest which part goes where?

---

### Post by sanderd17 on 2011-08-21
Normally, you want things that are read often, but not written often on you SSD, and other things on your HDD.

I don't have a very clear advise to you, but some googling should help. Look at this thread: [http://ubuntuforums.org/showthread.php?t=1664065](http://ubuntuforums.org/showthread.php?t=1664065)

---

### Post by linuxuser12345 on 2011-08-21
I am still debating on whether I should go and get the SSD also. I am planning on getting an HDD like this:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16822136892](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136892) plus an HDD fan

Is it really worth it to pay the extra $100 to get a 60GB SDD for the filesystem?

---

### Post by dino99 on 2011-08-21
if it boots in 5 seconds instead of 10 seconds, is that change your life ?

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by linuxuser12345 on 2011-08-21
Is anything much faster, other than boot time?

---

### Post by sanderd17 on 2011-08-21
Everything that needs your HDD is faster. So starting a program like libreoffice would be faster, but once a program is in RAM, the speed will remain as it used to be.

---

### Post by oldfred on 2011-08-21
I also am getting an SSD soon, but I look as it as a luxury item. It will not speed up my typing nor my download speeds from the Internet. I do not compile programs and do not load lots of programs at once.

But I also believe in having a fully bootable system on one drive and on every drive. So I would only move data to a different drive and keep the entire system & /home on the SSD, but all data normally in /home would be on other drives.

Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.

---

### Post by linuxuser12345 on 2011-08-21
Is there that much of a difference between a SATA III SSD and HDD?

---

### Post by sanderd17 on 2011-08-21
> **linuxuser12345 said:**
> Is there that much of a difference between a SATA III SSD and HDD?

A HDD is seriously limited by it's rotation speed (since it's a real disk). An SSD doesn't have that problem, and there SATA III could even become the bottleneck.

[http://ssd.toshiba.com/benchmark-scores.html](http://ssd.toshiba.com/benchmark-scores.html)

---

### Post by stefangr1 on 2011-08-21
> **linuxuser12345 said:**
> Is there that much of a difference between a SATA III SSD and HDD?

Yes, there is actually, SSDs are much faster. And dino99, if you're an impatient person like myself it will change your life (a little) :).

With an SSD the system becomes much more responsive. I would say the improvement in boot time isn't the most important thing (though it's significant), whats more important is that with an SSD virtually every application starts rightaway. Once you click it it's just there.

It's possible to mount different parts of the filesystem in different locations. Though I haven't tried 11.04 yet, this used to be possible even with the Live-CD install (you need to select partition manually somewhere in the process). You could for example mount / on your ssd and /home on your hdd. Or, for example if you have a large archive with media you could put / on the ssd and have your hdd mounted in /media/something.

---

### Post by linuxuser12345 on 2011-08-21
Is there much of a difference between a SATA II SSD and a SATA III SSD?

---

### Post by sanderd17 on 2011-08-21
That depends on the SSD I guess. There are SSDs in different speed classes. If the speed of the SSD is slower than sata II, than there is no need for sata III.

---

### Post by stefangr1 on 2011-08-21
> **linuxuser12345 said:**
> Is there much of a difference between a SATA II SSD and a SATA III SSD?

If you buy a midrange SSD it won't matter, as the 300MB/s max troughput of SATAII isn't limiting the performance. Somewhat faster SSDs that max out around 500MB/s need SATAIII for max performance. The difference between a HDD an SSD that does not exeed SATAII speeds is generally much larger than the performance difference between the fastest SATAII SSD and the fastest SATAIII SSD.

---

### Post by docbop on 2011-08-21
Id say forget the SSD and buy more RAM that benefits everything.

---

### Post by linuxuser12345 on 2011-08-21
I have another question: If I have the filesystem on my SSD and the home folder on the HDD, will my computer be much different at all than having everything on the HDD anyways?

---

### Post by stefangr1 on 2011-08-21
> **linuxuser12345 said:**
> I have another question: If I have the filesystem on my SSD and the home folder on the HDD, will my computer be much different at all than having everything on the HDD anyways?

Programs will stil benefit from the SSD, but if you open a file from you home folder it won't open any faster.

> Id say forget the SSD and buy more RAM that benefits everything.

That depends on the definition of "everything". My experience is that once you have enough RAM (say 4GB) more RAM doesn't add much. An SSD will.

---

### Post by linuxuser12345 on 2011-08-21
I think I am going to get both a SATA III SSD and HDD, and put most everything on the SSD except for the videos and music: The biggest space-wasters. This way, I get the awesome speed to do everyday things and get business done, yet have a large second drive specifically for the less important stuff, like videos, music, and other multimedia files (besides pictures). Does that sound like a good idea?

---

### Post by YesWeCan on 2011-08-21
If you want all your storage to be fast you will do better in terms of GB/$ to use hard disks in a striping arrangement, like RAID0. Use a slow disk for backup. Or use a RAID10.

Eg: a good 1TB drive costs about US$60. A good 120GB SSD costs about $200.

SSD, 120GB = $200 = $1.70 / GB
RAID0, 2000GB = $120 = $0.06 / GB
RAID10, $0.12 / GB

So an SSD is 28x more expensive per GB than a hard disk RAID0 and 14x more than RAID10.

In terms of speed I'm not entirely sure. I would expect a good SSD to be faster than RAID0...but...some SSDs are faster at read than write. And then there is the issue than in practice (unless you are very rich) maybe less than 10% of your storage will be on SSD anyway so the system will be slower accessing most of your data.

So I decided to invest in RAID10 and lots of RAM.

---

### Post by linuxuser12345 on 2011-08-21
Where would I find RAID?

---

### Post by linuxuser12345 on 2011-08-21
> **YesWeCan said:**
> And then there is the issue than in practice (unless you are very rich) maybe less than 10% of your storage will be on SSD anyway so the system will be slower accessing most of your data.

Well, I probably won't have a lot of videos and music to use often: I just want a big hard drive just to be sure I have enough space ;D

---

### Post by sanderd17 on 2011-08-22
> **YesWeCan said:**
> If you want all your storage to be fast you will do better in terms of GB/$ to use hard disks in a striping arrangement, like RAID0. Use a slow disk for backup. Or use a RAID10.

Eg: a good 1TB drive costs about US$60. A good 120GB SSD costs about $200.

SSD, 120GB = $200 = $1.70 / GB
RAID0, 2000GB = $120 = $0.06 / GB
RAID10, $0.12 / GB

So an SSD is 28x more expensive per GB than a hard disk RAID0 and 14x more than RAID10.

In terms of speed I'm not entirely sure. I would expect a good SSD to be faster than RAID0...but...some SSDs are faster at read than write. And then there is the issue than in practice (unless you are very rich) maybe less than 10% of your storage will be on SSD anyway so the system will be slower accessing most of your data.

So I decided to invest in RAID10 and lots of RAM.


Does RAID make that much of a difference? You have multiple hard disks, so reading and writing can happen simultanously, but you also have to read or write every bit twice (or more, depending on the sort of RAID). So that means if you have 6 disks in RAID, and the data that you need is perfectly balanced over those 6 disks, you get get 3 times the speed that you would have from one disk. If your data is very bad balanced (you need to access one disk for all data), than your speed won't increase at all. So that's OK for throughput, a little benefit (in the average case), but not so spectacular (considering you need a lot of disks). And for desktop computers, the latency is also important. And latency for RAID disks is worse than for single HDDs (again because two disks need to be accessed, so you get the latency of the slowest one). 

The main reason why people use RAID is for automated backups. In the most cases, when one disk goes down in a RAID, you just replace that disk with an empty one and the server will never know that data was missing.

Unless hybrid RAID is different, I don't see a lot of speed advantages in RAID.

---

### Post by stefangr1 on 2011-08-22
I would strongly advice against RAID 0 (striped), because if something in the array fails you could lose all your data. For RAID10 you would need 4 disks, and failure is still a risk.

Also, random read/write performance of an SSD is 10-20 times that of an HDD, while even continued read/write is easily 4 times as fast. So RAID won't give you any of the performance benefits of an SSD.

I very much agree with the OP's plan to put the OS and programs on the SSD and music/movies on an HDD. I have this same setup (so I might be a bit biased), and at least it works well for me.

---

### Post by YesWeCan on 2011-08-22
> **sanderd17 said:**
> Does RAID make that much of a difference? You have multiple hard disks, so reading and writing can happen simultanously, but you also have to read or write every bit twice (or more, depending on the sort of RAID). So that means if you have 6 disks in RAID, and the data that you need is perfectly balanced over those 6 disks, you get get 3 times the speed that you would have from one disk. If your data is very bad balanced (you need to access one disk for all data), than your speed won't increase at all. So that's OK for throughput, a little benefit (in the average case), but not so spectacular (considering you need a lot of disks). And for desktop computers, the latency is also important. And latency for RAID disks is worse than for single HDDs (again because two disks need to be accessed, so you get the latency of the slowest one). 

The main reason why people use RAID is for automated backups. In the most cases, when one disk goes down in a RAID, you just replace that disk with an empty one and the server will never know that data was missing.

Unless hybrid RAID is different, I don't see a lot of speed advantages in RAID.

RAID0 using two disks will double the average transfer rate of a single disk: [http://www.hardwaresecrets.com/article/Does-RAID0-Really-Increase-Disk-Performance/394/3](http://www.hardwaresecrets.com/article/Does-RAID0-Really-Increase-Disk-Performance/394/3)

---

### Post by YesWeCan on 2011-08-22
> **stefangr1 said:**
> I would strongly advice against RAID 0 (striped), because if something in the array fails you could lose all your data. For RAID10 you would need 4 disks, and failure is still a risk.

Also, random read/write performance of an SSD is 10-20 times that of an HDD, while even continued read/write is easily 4 times as fast. So RAID won't give you any of the performance benefits of an SSD.

I very much agree with the OP's plan to put the OS and programs on the SSD and music/movies on an HDD. I have this same setup (so I might be a bit biased), and at least it works well for me.

[http://blogs.msdn.com/b/jjameson/archive/2011/03/11/disk-benchmarks-ssd-vs-quot-raptor-quot-vs-raid.aspx](http://blogs.msdn.com/b/jjameson/archive/2011/03/11/disk-benchmarks-ssd-vs-quot-raptor-quot-vs-raid.aspx)

An SSD is going to be more reliable than a mechanical disk (although SSDs wear out). Either regular backups or mirroring make any difference unimportant, at least to me.

---

### Post by TheOneEyedMan on 2011-11-10
I am currently use two hard drives, one mounted as / and the other a larger one as /home. I've been thinking about buying an SSD to replace the one mounted on /. Currently, but withl all the applications installed on /, I have already used 144G on that drive so I'd need a fairly expensive SSD to make that work. But if I were to further split that drive up I don't know what should go on the SSD and what on the HD.

---

