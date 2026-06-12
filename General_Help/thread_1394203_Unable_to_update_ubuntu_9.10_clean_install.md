---
title: "Unable to update ubuntu 9.10 clean install"
date: 2010-01-30
forum: General Help
---

### Post by pbhole on 2010-01-30
Hi,
Today I installed Ubuntu 9.10 on VirtualBox (and VMware too). I am not able to get updates for it. When I press Reload in Synaptic Package Manager it says:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out

There is no problem with my LAN and internet setup as I tried installing Ubuntu 8.10 and 9.04 on same VirtualBox (and VMware) and I was able to get updates. Please help.

Thanks,
pbhole

---

### Post by Zorgoth on 2010-01-30
I think i have had a similar bug.  I think you will find that sometimes updates will work and sometimes they won't.

---

### Post by pbhole on 2010-01-30
In my case the update never worked with 9.10.

---

### Post by gmargo on 2010-02-01
> W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...ic/Release.gpg]("http://archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg")  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed  outThe "1.0.0.0" tells something - you may have a DNS problem.

I get considerably different addresses for archive.ubuntu.com:
> $ host archive.ubuntu.com
archive.ubuntu.com has address 91.189.88.46
archive.ubuntu.com has address 91.189.88.45
archive.ubuntu.com has address 91.189.88.30
archive.ubuntu.com has address 91.189.88.40

---

