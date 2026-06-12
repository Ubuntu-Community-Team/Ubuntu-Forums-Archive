---
title: "GCC for LTS"
date: 2011-10-08
forum: General Help
---

### Post by Jack Waugh on 2011-10-08
How does one reach those who decide what version of gcc and friends to include for the Long-Term Support (LTS) release of Ubuntu?  What are the criteria for determining whether a defect in some tool is bad enough to justify looking for a better version of that tool for LTS Ubuntu?

LTS currently has gcc 4.4.3, which has a defect in its optimization.  I don't know the defect report number, but I know the problem exists and other people mention it.  Compiling ruby 1.8.6-p399 demonstrates the defect in gcc.  The symptoms go away if one turns optimization off.  This is known in the Ruby community.

---

### Post by dcstar on 2011-10-08
> **Jack Waugh said:**
> How does one reach those who decide what version of gcc and friends to include for the Long-Term Support (LTS) release of Ubuntu?  What are the criteria for determining whether a defect in some tool is bad enough to justify looking for a better version of that tool for LTS Ubuntu?

LTS currently has gcc 4.4.3, which has a defect in its optimization.  I don't know the defect report number, but I know the problem exists and other people mention it.  Compiling ruby 1.8.6-p399 demonstrates the defect in gcc.  The symptoms go away if one turns optimization off.  This is known in the Ruby community.

Ubuntu releases only have the package versions used at the time of release, only Security Updates to these versions are released over the support lifespan of the LTS.

If you want later versions of packages from subsequent Ubuntu releases, enable the "Proposed" & "Backports" repositories and you **might** get a later version.

You can also try to manually install packages from later Ubuntu releases from this site:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

