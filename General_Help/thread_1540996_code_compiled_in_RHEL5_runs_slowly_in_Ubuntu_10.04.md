---
title: "code compiled in RHEL5 runs slowly in Ubuntu 10.04"
date: 2010-07-28
forum: General Help
---

### Post by amastbaum on 2010-07-28
I manage a small cluster that I'm trying to migrate from RHEL5 to Ubuntu 10.04. Doing this requires that some old software, which was compiled in RHEL, must run happily on both platforms. I'm not recompiling it.

After some trial-and-error library-hunting, the code now runs in Ubuntu, but is painfully *slow*, with top reporting ~50% iowait.

The process is reading data from an NFS mount served from Solaris/ZFS, a potential bottleneck, but this is not a problem in RHEL. Furthermore, my other tests show Ubuntu as marginally faster in NFS reads.

Can anyone think of a reason why software might do something like this? I'd think that the inevitable library-version mismatches would cause failure, not sluggishness.

Any thoughts or suggestions?

Thanks,
Andy

---

