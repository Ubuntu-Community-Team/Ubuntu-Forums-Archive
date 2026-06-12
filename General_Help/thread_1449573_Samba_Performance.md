---
title: "Samba Performance"
date: 2010-04-08
forum: General Help
---

### Post by arloth on 2010-04-08
I've noticed some odd issues with samba recently.  The performance between windows based clients, and linux based clients is huge, and not in a good way.  

Samba transfers to windows based machines run at about 15-17MB/s.
Samba transfers to other Linux based machines (all Ubuntu 9.10 atm), run at about 3-4MB/sec.
using SCP from one linux machine to another yields speeds of about 31MB/s.

I can't give too much data on how it used to perform, but I distinctly remember being able to burn DVDs at 12x without running the buffer down on the linux clients.  There has to be a reason for such a huge performance delta between the two.  One would expect the Samba->Samba transfers to be the fastest, but they're quite slow instead.

I'm using a Netcell PCI based raid card on the samba server, so I'm not expecting blinding speeds but 4MB/s is completely unacceptable.

Can anyone explain this? Is smbd 3.4.7 in 10.04 any better?  9.10 still uses 3.4, so no performance/security fixes since then at least.

---

### Post by dcstar on 2010-04-08
> **arloth said:**
> 
.........
Can anyone explain this? Is smbd 3.4.7 in 10.04 any better?  9.10 still uses 3.4, so no performance/security fixes since then at least.

Are you running 7.10 - as your profile says - or 9.10?

---

### Post by arloth on 2010-04-08
> **dcstar said:**
> Are you running 7.10 - as your profile says - or 9.10?

No, I just haven't updated my profile recently. ;)

I will probably try manually updating samba to 3.5.2 on a spare computer or two and see how the performance goes.  Samba 3.4.7 is what's currently listed for 10.04 on distrowatch, while the Samba website lists it as being a historical release.  

I hesitate to do this for fear i might enter the awful world of dependency hell, but the current performance I'm getting is unacceptable.  imho, there is no good reason for a windows client to be faster than a samba based one.

Are there any repositories with Samba in them like there are for Wine & KDE?

---

### Post by arloth on 2010-04-08
Found a repository, [https://launchpad.net/~polslinux/+archive/ppa](https://launchpad.net/~polslinux/+archive/ppa)

I'll see how it does later tonight.

---

### Post by arloth on 2010-04-09
Upgrading to 3.5.2 resulted in little to no change of performance.  After doing some more digging, it seems other people have noticed this abysmal performance between other Ubuntu machines.  See here, [http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8980545](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8980545)   It's listed as solved, but switching to NFS isn't really fixing the problem, it's just dodging it. ;)

I also tried disabling ipv6, as some have said that it has made things run slower, but no change in performance was noticed either. I did notice the CIFSMaxBufSize option in the manual page and on their post. Based on what the manual says it won't request more than 16K at once without changing it on module load time.  Maybe somebody could point me in the right direction as to how to change this properly?

I will probably switch to using NFS for a while as well, this issue will more than likely take a while to sort out, but I would still like an actual solution to this problem.

---

