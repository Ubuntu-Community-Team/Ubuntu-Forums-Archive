---
title: "Kernel 3.0\3.2 on Lucid 10.04... how to?"
date: 2012-01-28
forum: General Help
---

### Post by TheNessus on 2012-01-28
So I have Lucid and I want to have kernel 3.0 or 3.2 on it. 

Reasons: Kernel 3.2 enables me to increase\decrease brightness, as there is a bug that is not fixed until 3.0 with my specs. Also, random freezes that can only be solved with hard reset is solved in 3.0+. I know this because I used 11.10 and 12.04-testing without both issues affecting me, at last. But resorted back to 10.04 due to other issues.

Would like to know if this is possible. If so, how.
thanks.

---

### Post by Karlchen on 2012-01-28
Hello, TheNessus.

If my Synaptic tells the truth - after updating the list of available packages - the latest kernel available for Lucid Lynx seems to be 3.0.0.15.
I cannot make any statement on how well it co-operates with the rest of Lucid Lynx, because my system is still on kernel 2.6.32-38.

Kind regards,
Karl

---

### Post by Double.J on 2012-01-28
+1 

The 3.0.0.15 kernel is what has been back ported to lucid. If you want to go to the third generation kernel, this would be the recommended kernel. A lot of people did have problems (myself included) with this kernel however that weren't experienced in 2.6.3X kernels - hence the amount of kernel upgrading that's been going on of late - a year a go no where near as popular ;)

In theory there's nothing to stop you downloading the precise 3.2 deb's and dpkg'ing them - it *should* work, although this is of course untested and without guarantee. The backports are designed to make running newer software easier, so I'd try that first ;)

All the best :)

---

### Post by Double.J on 2012-01-28
If you did need a newer kernel than this, have a look here;
[How Open Source Guide]("http://www.howopensource.com/2011/08/how-to-install-linux-kernel-3-1-rc2-oneiric-in-ubuntu-11-04-10-10-and-10-04/") - all theoretically simples!

When getting your packages, be sure to use a stable kernel - save 3.3 testing to you precise system ;)

---

### Post by pbrane on 2012-01-28
I would recommend you look at this. [https://wiki.ubuntu.com/KernelTeam/GitKernelBuild]("https://wiki.ubuntu.com/KernelTeam/GitKernelBuild") I have used this method for several years and it works great. Pay attention to the section titled "*Using Ubuntu Kernel Configuration*". Also I usually down the tarball of the latest stable to compile, I don't *git clone* the mainline tree. But you can if you want.

I'm running the 3.2.2 kernel now.

---

