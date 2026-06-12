---
title: "apt-mirror problem with ubuntu in virtualbox on windows xp"
date: 2010-04-01
forum: General Help
---

### Post by prodev on 2010-04-01
Hi!

Sorry for the long post, I just couldn't get all the relevant details in a shorter space...

I'm trying to create a local copy of the Ubuntu repositories for use with an offline laptop. My machine at work is running windows xp and creating a dual-boot on it is not allowed. So I installed Karmic within VirtualBox and is working well. I got the proxy configured for synaptic and apt-get (and bash) in addition to recognizing my external USB hard disk on which the repositories should be copied.

Before I left yesterday I started the apt-mirror (after configuring it for a local ftp mirror on the company LAN). It gave the usual "Downloading 98 index files using 10 threads.." message. However, this morning it had only downloaded 2.4 GB from the 34 GB it should!

The ftp site is fully operational and the LAN speed is 1Gbps - all working very well. The utilization is however VERY poor. It seems that a some data is downloaded as a burst and then nothing happens for an arbitrary long time. This is only for apt-mirror, because the browser, synaptic and apt-get all seem to be working as expected.

I've tried looking at the apt-mirror script source and changed some of the wget parameters and also reduced the threads from 10 down to 1, but seem to only have made things worse.

Can anyone provide some direction?

---

