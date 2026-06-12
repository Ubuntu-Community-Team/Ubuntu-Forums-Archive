---
title: "Getting Kernel Information"
date: 2011-03-08
forum: General Help
---

### Post by towheedm on 2011-03-08
Ok, so I have quite a few different distros installed presently.  My main OS is Maverick.

I know that I can get information from my running kernel using the uname command.

My question is, how can I retrieve the kernel information from the  other distros without booting into them?

For example, I have Debian installed on /dev/sdd1 with two kernels in /boot.  How do I go about getting the information from these kernels similar to what uname gives?

---

### Post by dcstar on 2011-03-09
> **towheedm said:**
> Ok, so I have quite a few different distros installed presently.  My main OS is Maverick.

I know that I can get information from my running kernel using the uname command.

My question is, how can I retrieve the kernel information from the  other distros without booting into them?


You can't. Actual kernel information is embedded inside each kernel and only available when the kernel is loaded.

You can **assume** that the names of the kernels in those other systems actually reflect what is inside those kernels and simply read the file names of the kernels in their respective file locations in their partitions.

---

