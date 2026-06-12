---
title: "Computer acting slow when reading/writing files from/onto disk"
date: 2010-09-27
forum: General Help
---

### Post by DeMus on 2010-09-27
Hi,
Whenever I am busy reading or writing large files, or large sum of files, my computer is unresponsive. Screens are getting greyed-out and I just can sit there and wait until the reading/writing is done.
This is not caused by the CPU which is overstressed because it is not. Look at the attachments and you will see the CPU is used for about 20%. When these pictures were captured the computer was using hellanzb to unrar a long list of rar-files.
When you look at my signature you see the computer is not bad at all, just disk-access is slow. I can transfer files with a maximum speed of 30MB/s. Is that normal or is it very slow? I don't know the numbers. I have 2 SATA disks.
O.S. is Mint 9-Isadora, based on Ubuntu 10.04 and I use the 64-bits version.
If you need more info just let me know and I will supply it.

Thanks in advance.

---

### Post by mikewhatever on 2010-09-27
It is a known problem, and it got some attention lately.
[http://www.phoronix.com/scan.php?page=news_item&px=ODQ3OQ](http://www.phoronix.com/scan.php?page=news_item&px=ODQ3OQ)
Not sure anything can be done for Lucid.

---

### Post by DeMus on 2010-09-28
> **mikewhatever said:**
> It is a known problem, and it got some attention lately.
[http://www.phoronix.com/scan.php?page=news_item&px=ODQ3OQ](http://www.phoronix.com/scan.php?page=news_item&px=ODQ3OQ)
Not sure anything can be done for Lucid.

My problem is not solved yet but thanks to you I know something is going on about it. Thank you for your answer. I will keep monitoring it.

---

### Post by DeMus on 2010-10-05
I downloaded kernel 2.6.35 and I do believe it is a bit better but still not 100%.
Anyone else who can help me with this?

---

### Post by addy digit on 2010-10-06
One thought... if you had your backup drive installed when you got your virus, it's quite possible that the virus had jumped onto your backup. Then after reformatting the main drive it just jumped back onto the main drive from the backup. I've seen trojans do this many times - even jump to/from thumb drives.
You can mail me if you want and I'll see if I can help puzzle it out...
Good luck,:)

---

### Post by steve021 on 2010-10-06
which antivirus is installed on your pc. some antivirus slow down you spped like avast, AVG
another problem can be you rams . change it and try . hope you will get your desired task

---

### Post by NightwishFan on 2010-10-06
Try using the deadline i/o scheduler. I have been using that to good results. Just add this code to the grub boot options:
```
elevator=deadline
```

> **steve021 said:**
> which antivirus is installed on your pc. some antivirus slow down you spped like avast, AVG
another problem can be you rams . change it and try . hope you will get your desired task

It is a specific problem I believe, and not much to do with userspace applications.

---

### Post by DeMus on 2010-10-06
> **addy digit said:**
> One thought... if you had your backup drive installed when you got your virus, it's quite possible that the virus had jumped onto your backup. Then after reformatting the main drive it just jumped back onto the main drive from the backup. I've seen trojans do this many times - even jump to/from thumb drives.
You can mail me if you want and I'll see if I can help puzzle it out...
Good luck,:)

????
Who said anything about a virus? It can't be a virus. I have had a couple of different installations these past months and they all had it. Also it is a well-known problem which will be taken care of in Mavarick, so I hear.
The problem is I don't want to skip to Maverick, I want to keep using this LTS version for a longer period of time.

---

### Post by DeMus on 2010-10-06
> **NightwishFan said:**
> Try using the deadline i/o scheduler. I have been using that to good results. Just add this code to the grub boot options:
```
elevator=deadline
```



It is a specific problem I believe, and not much to do with userspace applications.

Thank you Nightwishfan, I will try that. Will let you know how the results are.

---

### Post by DeMus on 2010-10-06
Nightwishfan, I tried your solution and I believe it is a bit better, but just a bit. Especially Banshee turns grey when I , for example, unrar a long list of rar files (which means reading and writing a lot of data). CPU load is not high so it's not caused by that.

---

### Post by NightwishFan on 2010-10-06
I have this problem as well. Using deadline helps some, as you said, I agree. It is the only solution I found that had merit. :(

---

### Post by DeMus on 2010-10-10
I was wondering, in System Monitor it is possible to see what the CPU(s) is (are) doing and what happens on the network connection. Is there also a program to see what is happening with the hard disks? I mean how data do they have to read/write? Would be interesting in this case.

---

### Post by NightwishFan on 2010-10-10
I believe there is one called "iotop".

---

### Post by DeMus on 2010-10-10
> **NightwishFan said:**
> I believe there is one called "iotop".

Once again thank you. This program is similar to top and htop, only now for diskaccess. Great, thanks.

---

### Post by NightwishFan on 2010-10-10
I will share anything I discover with you here, I am interested in solving this as well. I actually learned there was a patched kernel for io performance however it did not help me much. Perhaps you will have better results or could contribute here.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/131094](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/131094)

---

### Post by NightwishFan on 2010-10-20
Also, try using Noop as well "elevator=noop". That may in some circumstances help as well.

---

