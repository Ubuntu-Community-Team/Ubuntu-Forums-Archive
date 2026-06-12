---
title: "Virus clearing questions"
date: 2009-09-15
forum: General Help
---

### Post by keevill on 2009-09-15
I do not have much success in this forum getting solutions but I will try one more time.
1. Is it really really necessary to have an antivirus prog with Linux ( Ubuntu 9.0.4 )?
2. I have a Win2k box with a virus on it - can I boot up into 'test Ubuntu' and clear it ? Normally, I would take out the hard disk and connect it to another Win box and scan/remove that way.

---

### Post by MelDJ on 2009-09-15
> **keevill said:**
> I do not have much success in this forum getting solutions but I will try one more time.
1. Is it really really necessary to have an antivirus prog with Linux ( Ubuntu 9.0.4 )?
2. I have a Win2k box with a virus on it - can I boot up into 'test Ubuntu' and clear it ? Normally, I would take out the hard disk and connect it to another Win box and scan/remove that way.

1. no
2. yes
:KS

---

### Post by coolclassic on 2009-09-15
Linux is inherently safe from viruses so there is no need to install a virus checker unless you are constantly exchanging files with a windows system. Although linux may not get infected in does not stop the virus being transfered to a windows system.

You can scan window partitions using software like ClamAV. This will detect and remove any virus.
[http://www.clamav.net/](http://www.clamav.net/)

---

### Post by x33a on 2009-09-15
1. you can have a virus scanner on a linux machine, to scan for windows viruses, to prevent passing them to other windows machines (example, on a network). your linux machine won't get infected even if you don't have an anti-virus.

2. through linux you'll have to remove the viruses manually, because not many good scanners are available for linux.

---

### Post by ccline19 on 2009-09-15
Is it harder for viruses or trojans to infect a Linux machine, yes however, it never hurts to be protected from that one time someone does create a virus that targets a linux platform. Since most Linux users think they are 100% safe you could be infected one day and not even know it. Turning a blind eye to the possibility is more dangerous than the virus.

---

### Post by ankspo71 on 2009-09-15
Do you know where and what the virus is? If not you will probably want to download and install a linux virus scanner on your live CD. 

I'll be back to let you know if a certain virus scanner for linux will be able to scan a windows/drive partition. I have to get on my wife's pc to see.

James.

---

### Post by MelDJ on 2009-09-15
> **ccline19 said:**
> Is it harder for viruses or trojans to infect a Linux machine, yes however, it never hurts to be protected from that one time someone does create a virus that targets a linux platform. Since most Linux users think they are 100% safe you could be infected one day and not even know it. Turning a blind eye to the possibility is more dangerous than the virus.

actually you are right. proved by bliss. but the fact that many programs are open source and the way linux is structured, it is hard to make a virus which can harm linux. read this [http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)

---

### Post by ajc37 on 2009-09-15
What anti-virus do you have?, you can get avast for linux

ajc37

---

### Post by bruno9779 on 2009-09-15
Clam AV is made ONLY to scan for Windose viruses.

There have been dangerous linux viruses a few years ago, but none since.
Being that AVs work with virus signatures (the virus gets neutralized by SW developers and the data needed to do this becomes a signature) so it is useless to install a Linux AV if there aren't any signatures for it.

On a side note, I have recently seen an Ubuntu box damaged by a crossover trojan (java)

---

### Post by bruno9779 on 2009-09-15
sorry for the double posting

This is a ver interesting read too:

[The short life and hard times of a Linux virus]("http://librenix.com/?inode=21")

> Linux applications and system software is almost all open source. Because so much of the Linux market is accustomed to the availability of source code, binary-only products are rare and have a harder time achieving a substantial market presence. This has two effects on the virus. First, open source code is a tough place for a virus to hide. Second, for the binary-only virus, a newly compiled installation cuts off a prime propagation vector.

---

### Post by ankspo71 on 2009-09-15
Hi Again,

Sorry. I tried Avast for Linux on my wife's winXP computer, and I was not able to scan her windows hard drive with an Ubuntu 9.04 live disk. It didn't even show the hard drive.

Hope someone here has a good suggestion. ClamAV?
James

---

### Post by bruno9779 on 2009-09-15
I think you should have a look at this:
[URL="http://njlinux.blogspot.com/2008/01/virus-scan-windows-using-linux-live-cd.html"]
Virus scan Windows using a Linux live CD[/URL]

It is a pretty easy to follow howto that uses knoppix and I'd go with that, but it should work with ubuntu as well. I haven't had a chance to try that out, as my home is MS free, but I have everything ready, and scanning a Dummy NTFS partition isn't fun.

If it works for you please post results (I would like to know what virus did your GF get too...)

---

### Post by lisati on 2009-09-15
Ever noticed that discussions like this often get side-tracked by the topic Linux viruses? As I understand it, the OP wants to use Ubuntu as one of the tools for dealing with malware on a Windows machine. 

Edit: I see nothing wrong with researching your options for malware protection and "disaster recovery" on Ubuntu.

---

