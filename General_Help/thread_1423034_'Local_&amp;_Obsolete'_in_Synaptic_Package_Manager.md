---
title: "'Local &amp; Obsolete' in Synaptic Package Manager"
date: 2010-03-06
forum: General Help
---

### Post by Ron W on 2010-03-06
Hello

I have a long list of files like the following examples mentioned in the Synaptic Package Manager's 'Installed (local or obsolete)':

linux-headers-2.6.24-18
linux-headers-2.6.24-18-generic
linux-image-2.6.24-18-generic

with the last two digits ranging from 14 to 23.

I currently have Kernel Linux 2.6.24-26-generic loaded (according to System->Administration->System Monitor->'System' tab) [I'm using 8.04 LTS].

I'm hesitating in removing them because I assume that the Synaptic Package Manager would remove these when doing the upgrades. My suspicion is that these are still needed for later versions and removing them would cause a few problems to say the least.

Am I safe to either 'Remove' or 'Completely Remove'?

It would be great to save all that space if these can be removed.

Thanks

Ron

---

### Post by Intrepid Ibex on 2010-03-06
They can be completely removed. The way Ubuntu handles new kernels is just that it keeps the old ones - often this is not a problem if you change your distribution every6 months but some people use Ubuntu (which I personally don't recommend) for like 3 years before switching to the new one.

When you keep the same distribution of Ubuntu for 3 years you will get quite a nice list of kernels - and for what, for you to sit back and say your hdd is getting filled?

You are safe to remove these - I'd recommend just to have the two latest ones if something should happend to your current kernel. In this case you could boot to the former one and fix the problem.

---

### Post by Ron W on 2010-03-07
Thanks for your clear and helpful advice, Intrepid.

I've done as you've suggested and now have a bit more space on my disk and more understanding of how Ubuntu works.

Thanks again

---

