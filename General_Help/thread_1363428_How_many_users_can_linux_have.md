---
title: "How many users can linux have?"
date: 2009-12-24
forum: General Help
---

### Post by shade5 on 2009-12-24
Hi.

I am wondering if it is possible to have an endless amount of users on a linux system.

---

### Post by nubalci on 2009-12-24
See [http://linuxgazette.net/issue98/pranevich.html](http://linuxgazette.net/issue98/pranevich.html).
But, over infinite time, yes :)

---

### Post by Specologic on 2009-12-24
Hi,

For example, I'm a new guy at Linux :P, and I'm loving it :P

Happy Christmas.

Regards

---

### Post by bodhi.zazen on 2009-12-24
The maximum number of groups / users is determined by the kernel.

See : [http://en.wikipedia.org/wiki/Linux_kernel](http://en.wikipedia.org/wiki/Linux_kernel)

Last paragraph (emphasis added by myself):

> Version 2.6.0 was released on 18 December 2003.[[50]]("http://en.wikipedia.org/wiki/Linux_kernel#cite_note-kern2p6-release-49") The 2.6 series of kernels is still the active series of stable kernels as of 1 December 2009. The development for 2.6.*x* changed further towards including new features throughout the duration of the series. Among the changes that have been made in the 2.6 series are: integration of [µClinux]("http://en.wikipedia.org/wiki/%CE%9CClinux") into the mainline kernel sources, [PAE]("http://en.wikipedia.org/wiki/Physical_Address_Extension") support, support for several new lines of [CPUs]("http://en.wikipedia.org/wiki/CPU"), integration of [ALSA]("http://en.wikipedia.org/wiki/Advanced_Linux_Sound_Architecture") into the mainline kernel sources, **[SIZE=2]support for up to 2^32 users (up from 2^16), support for up to 2^29 process IDs (up from 2^15)[/SIZE]**, substantially increased the number of device types and the number of devices of each type, improved 64-bit support, support for [filesystems]("http://en.wikipedia.org/wiki/Filesystem") of up to 16 [terabytes]("http://en.wikipedia.org/wiki/Terabytes"), in-kernel [preemption]("http://en.wikipedia.org/wiki/Preemption_%28computing%29"), support for the Native POSIX Thread Library, [User-mode Linux]("http://en.wikipedia.org/wiki/User-mode_Linux") integration into the mainline kernel sources, [SELinux]("http://en.wikipedia.org/wiki/SELinux") integration into the mainline kernel sources, [Infiniband]("http://en.wikipedia.org/wiki/Infiniband") support, and considerably more. Also notable are the addition of several filesystems throughout the 2.6.*x* releases: [FUSE]("http://en.wikipedia.org/wiki/Filesystem_in_Userspace"), [JFS]("http://en.wikipedia.org/wiki/JFS_%28file_system%29"), [XFS]("http://en.wikipedia.org/wiki/XFS"), [ext4]("http://en.wikipedia.org/wiki/Ext4") and more. Details on the history of the 2.6 kernel series can be found in the ChangeLog files on [the 2.6 kernel series source code release area]("http://www.kernel.org/pub/linux/kernel/v2.6/") of [kernel.org]("http://www.kernel.org/").

Note those numbers are 2 to the 32 power not "232"

---

