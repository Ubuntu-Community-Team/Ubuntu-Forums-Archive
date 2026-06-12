---
title: "Kernel updated in one PC, but not in the other. Why?"
date: 2011-02-08
forum: General Help
---

### Post by apollo_el on 2011-02-08
Hello people,

Ubuntu 10.10 on both PC's.

One is updated to kernel 2.6.35.25, but the other one
does not give me any updates for kernels..so it still has 2.6.35.24. I don't understand this. Help anybody?

Thanks in advance :-)

---

### Post by WorMzy on 2011-02-08
Your repo package information may be out-of-date. Open a terminal and run

```
sudo apt-get update
```

or click the refresh button in Synaptic Package Manager.

---

### Post by b0b138 on 2011-02-08
are they both pointed to the same mirror? Some are behind

[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

---

### Post by apollo_el on 2011-02-08
> **WorMzy said:**
> Your repo package information may be out-of-date. Open a terminal and run

```
sudo apt-get update
```or click the refresh button in Synaptic Package Manager.

I always do this...it's not the problem (sudo apt-get update)
Thanks for the input, though.

p.s. I can see the newer kernel in Synaptics....the question remains..what's wrong and I don't get this via the sudo apt-get update/upgrade?

---

### Post by apollo_el on 2011-02-08
> **b0b138 said:**
> are they both pointed to the same mirror? Some are behind

[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

You mean in the /etc/apt/sources.list ?

---

### Post by gmargo on 2011-02-08
Try "apt-get dist-upgrade" or "aptitude full-upgrade" after doing the update.  If you just "upgrade" without the dist- or full-, then certain packages are held back, like the linux kernels.

---

### Post by dcstar on 2011-02-08
> **apollo_el said:**
> Hello people,

Ubuntu 10.10 on both PC's.

One is updated to kernel 2.6.35.25, but the other one
does not give me any updates for kernels..so it still has 2.6.35.24. I don't understand this. Help anybody?

Thanks in advance :-)

There are various options in Synaptic on what level of updates you want for the system, and what repositories are enabled for the system.

Unless these are **all** identical on both systems then their behaviour may well be different.

---

### Post by apollo_el on 2011-02-09
> **gmargo said:**
> Try "apt-get dist-upgrade" or "aptitude full-upgrade" after doing the update.  If you just "upgrade" without the dist- or full-, then certain packages are held back, like the linux kernels.


Thanks..I tried it, but still no difference in the kernel.

---

### Post by apollo_el on 2011-02-09
> **dcstar said:**
> There are various options in Synaptic on what level of updates you want for the system, and what repositories are enabled for the system.

Unless these are **all** identical on both systems then their behaviour may well be different.

I don't use much Synaptics...I'm more like a sudo apt-get update/upgrade guy (unless the update manager gets me first). Thus, I did not mess around with any settings in Synaptics. 

Only thing I can tell you is that one PC has a fresh install of Ubuntu 10.10 (just a couple of days ago) and the new kernel appeared as an update (update manager), whereas the other older one had originally Ubuntu 10.04 and then I upgraded to 10.10, last October, and the newer kernel won't appear with sudo apt-get (or for that matter in the update manager).

Never had such issues before, I must say. 

Thank you for your answers

---

### Post by apollo_el on 2011-02-09
Btw, I also had this idea today to cp the entire /etc/apt dir from the "unproblematic" new PC, to the older one which won't show the newer kernel as an update (via sudo apt-get); just to make things equal. Perhaps, a stupid idea...I'm not sure. still no change....hmmm....

---

### Post by gmargo on 2011-02-09
How about **diff**ing the two /etc/apt/ directories? (Although now that you've done a copy, this is probably a lost cause.)

---

### Post by apollo_el on 2011-02-10
> **gmargo said:**
> How about **diff**ing the two /etc/apt/ directories? (Although now that you've done a copy, this is probably a lost cause.)

Yes I should have diff'em before, perhaps. Problem remains. Maybe something is broken...is there some kind of component(s) I could re-install to fix this? (i've tried the update manager..but no difference).

---

### Post by b0b138 on 2011-02-10
Does it have the linux-image-generic and linux-generic package installed? As these point to the latest kernel package.  This would make some sense because 2.6.35-24 and 2.3.35-25 and different packages. Where 2.6.35-24.22 and 2.6.35-24.36 are the same package, just the later is an update.

---

### Post by apollo_el on 2011-02-10
> **b0b138 said:**
> Does it have the linux-image-generic and linux-generic package installed? As these point to the latest kernel package.  This would make some sense because 2.6.35-24 and 2.3.35-25 and different packages. Where 2.6.35-24.22 and 2.6.35-24.36 are the same package, just the later is an update.

It has the linux-image-generic 2.6.35-24.42 and similarly for linux-headers-generic. I can't see the linux-generic that you are talking about.

---

### Post by b0b138 on 2011-02-10
What happens if you ```
sudo apt-get install linux-generic
```

What version is linux-image-generic.  I just booted into maverick (haven't in awhile) and it says the installed version is 2.6.35.23.25 and the latest version is 2.6.35.25.32.

---

### Post by apollo_el on 2011-02-10
> **b0b138 said:**
> What happens if you ```
sudo apt-get install linux-generic
```What version is linux-image-generic.  I just booted into maverick (haven't in awhile) and it says the installed version is 2.6.35.23.25 and the latest version is 2.6.35.25.32.

The version I have is the one I gave above. However, you are right..running sudo like you said..starts :

*************************************************
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  linux-image-2.6.35-25-generic linux-image-generic
Suggested packages:
  fdutils linux-doc-2.6.35 linux-source-2.6.35 linux-tools
The following NEW packages will be installed:
  linux-generic linux-image-2.6.35-25-generic linux-image-generic
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 33.9MB of archives.
After this operation, 107MB of additional disk space will be used.
*************************************************


Of course, this would make sense given that I don't have any problems locating the packages (via Synaptic), the problem is that they won't come up as updates with sudo apt-get update/upgrade or in the Update Manager, for that matter.

Thanks for your answers :)

---

### Post by b0b138 on 2011-02-10
It looks like neither linux-generic or linux-image-generic were installed, and these point to the newest kernel. 2.6.35-24 is a different package than 2.6.35-25, which is why it wouldn't update to -25 without linux-image-generic.

Glad its worked out though \\:D/

---

### Post by apollo_el on 2011-02-11
> **b0b138 said:**
> It looks like neither linux-generic or linux-image-generic were installed, and these point to the newest kernel. 2.6.35-24 is a different package than 2.6.35-25, which is why it wouldn't update to -25 without linux-image-generic.

Glad its worked out though \\:D/

For future reference (in case some1 stumbles upon a similar issue), here's what I've done:

sudo apt-get install linux-generic (1)

but it notified me that linux headers were missing, so I installed the ones that told me to FIRST:

sudo apt-get install linux-headers-2.6.35-25-generic (2)

and then back to (1).


Special thanks to [b0b138]("http://ubuntuforums.org/member.php?u=485187"). Thanks a bunch Atlanta!
Though, I can't understand how this happened  :)!!!!

---

### Post by b0b138 on 2011-02-11
> **apollo_el said:**
> 
sudo apt-get install linux-headers-2.6.35-25-generic (2)

Make sure linux-headers-generic is installed. This will point to the newest headers that come out with the newest kernel :popcorn:

---

