---
title: "How to work-around repository of an expired LTS"
date: 2010-08-25
forum: General Help
---

### Post by shemuel on 2010-08-25
Hi all,

I am new to Ubuntu. My hardware platform is an old laptop built on an ATI motherboard and chips. It has 1.9G of RAM and 80G Hd. After months of trying distros here and there I have settled on Ubuntu 6.06 Dapper drake because it has a built-in module for my ATI Radeon 200m, it uses the hardware good enough without necessarily setting some Grub-time parameters like noapic, noapci, etc. 

But the LTS is already expired and I can no longer Synaptic for the applications that I am in dire need of. I have even tried to compile backward WinehQ 0.9.9 but it did not make, requiring me to update libs and gcc, which, aside from being over-engrossing I have no luxury of time for that. Also recent softwares are built upon newer kernels which Dapper cannot cope with.

Is there a way to obtain a DVD containing all the software compatible to Dapper that I can use offline and include it in the source.list paths?

Or, is there an online repository STILL available today, canonical or not, that provides a key so that I can still apt-get or synaptic to it?

Is there a work around that I can do of for my purpose?

I have spent two days already thinking about and tinkering but the result of my labor is unsatisfactory. 

Please help. Thanks ahead.

---

### Post by holycow131415 on 2010-08-25
I am confused, that computer doesnt sound old at all. Did you try the new LST via liveCD? 10.04.01 ? Im not really all pro here but i dont see why the new LST wouldnt carry over the version 6 features :)

---

### Post by amac777 on 2010-08-25
After the support period for a version ends, the repositories for the expired version are moved here:

[http://old-releases.ubuntu.com](http://old-releases.ubuntu.com)

If you need to keep using an old release, you can update your /etc/apt/sources.list to point to the above server and that will allow you to still install programs in the same ways you could when you the release was current. Of course, there will be no updates or security fixes to the old-releases, but at least they are there if you need to keep running them for some reason.

---

### Post by shemuel on 2010-08-26
Holycow, yes indeed, the RAM doesn't sound really that old, but ATI is truely a pain when it comes to free and open software. I have this laptop preinstalled with xp but when I migrated all my systems into Gnu/Linux this laptop was left behind after it failed to satisfy Linux Mint 5 and 6, as well as the three previous versions of Ubuntu. I only found chance to tinker with this again this time hoping to make it this time. Last year, I remember, openSolaris installed in this unit seamlessly but I didn't want to learn use solaris because it is not a totally free kernel (sort of social value).

Amac777 thank you for the link. I shall sure check this out with hope.

Thank you all.

sam

---

