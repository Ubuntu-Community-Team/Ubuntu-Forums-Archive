---
title: "Aptitude lists two copies of every package"
date: 2011-11-17
forum: General Help
---

### Post by pawanh on 2011-11-17
Every package repeats, and gets classified as a conflict to the other one. The only difference being that the second listed package does not have a description, and only the homepage is given in the description. Whenever I install a package the other one remains in the uninstalled category. Also all packages from one "group" seem to be incompatible with the other "group". I mean, if I install the package listed first among two similar named packages, I cannot install a dependency which is the second among its duplicates. I encounter this duplication in aptitude only, and not in Muon or Software Center.

---

### Post by yebyen on 2011-11-18
You are not the only one.

I also found [http://ubuntuforums.org/showthread.php?t=1883093](http://ubuntuforums.org/showthread.php?t=1883093)

Are you using a system that was upgraded to Oneiric 11.10?

I have a system that was cleanly installed (Oneiric 11.10) and it does the same thing.  In fact we have about ten of them.  My boss noticed the difference after he upgraded to Oneiric, I guess there is a chance that it was a problem on Natty also (maybe he just looked at aptitude after upgrading to see what was new?)

I just checked on a natty chroot that I've kept around, it does not do this.
So it must be some kind of a bug in oneiric.  Anyone know the resolution?

-Kingdon

---

### Post by awry on 2011-11-18
I have this problem, too, on several oneiric installs (one upgraded from natty, several installed using vmbuilder). No sign of any bug reports at Launchpad or Debian BTS. Confirm?

---

### Post by CrystalFire on 2011-11-19
I just upgraded to Ubuntu Oneiric 11.10 from Ubuntu Natty 11.04 and am also having the same issue. For now, installing the one with a description ( as opposed to the one w/o ) avoids conflicts, but a resolution would be nice.

Edit:

After reviewing the Synaptic Package Manager, it seems that the duplicates are in fact not an error, but simply a different version.

Am I correct in assuming that we are all using a 64 bit distribution?

---

### Post by pawanh on 2011-11-20
I am indeed running an Oneiric 64-bit clean install.:P

Shouldn't different versions be listed under the same name?

---

### Post by yebyen on 2011-11-22
No, I experienced the problem on a 32 bit variant.

I have it here again (it's back) with a freshly installed 32 bit oneiric, I will post again later about this problem.  However, I expect to see aptitude behaving the same way now that the machine has been wiped and installed freshly with Oneiric 11.10 (32 bit)

---

