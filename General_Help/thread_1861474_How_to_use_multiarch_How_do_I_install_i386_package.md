---
title: "How to use multiarch? How do I install i386 packages in 64bit 11.10?"
date: 2011-10-15
forum: General Help
---

### Post by OrangeEtzer on 2011-10-15
I know 11.10 has "multiarch" so that I can install i386 packages in the 64 bit version of the OS. However, I have no idea how to do it. I mean, I still get an error in the Software Center when I try to install an i386 .deb file or when I try to install a .bin or .rpm file through Terminal. What am I doing wrong?

---

### Post by Dark Shinobi on 2011-11-08
Thus far for me any attempts to install x86 libs required by x86 packages simply replaces all the x64 ones, completely breaking the package manager and completely screwing with the way ubuntu works. I have had absolutely no success in finding a solution to this problem, nor finding any solution on any forums anywhere. The old ia32 or 32 bit chroot is starting to look good compared to "multi-arch" right now :) At any rate though, I am glad they are implementing it even if it is broken at the moment. Hopefully it will be fixed through an update or on 12.04. Lets hope we find a solution soon!

---

### Post by oldos2er on 2011-11-08
Bug report here: [https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/852101?comments=all](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/852101?comments=all)

---

