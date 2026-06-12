---
title: "Lucid, official kernel 2.6.35 and fglrx"
date: 2011-02-26
forum: General Help
---

### Post by Anton K on 2011-02-26
Hello!
As it's easy to understand from the topic name, I use Ubuntu 10.04 and I'd like to boot the latest kernel (at the present moment it's 2.6.35-23) from Ubuntu repositories (not from Kernel PPA). I've installed this kernel with a help of two packages:

[LIST=1]
[*]linux-image-generic-lts-backport-maverick
[*]linux-headers-generic-lts-backport-maverick
[/LIST]
And the problem is FGLRX modules failed to build for the backported kernel. I think, it's concerned with the old version of Fglrx (2:8.723.1 for Lucid), which is unable to support newer kernels.

I've already read these threads:
[http://ubuntuforums.org/showthread.php?t=1546932](http://ubuntuforums.org/showthread.php?t=1546932) - but I prefer to leave installed fglrx and not to install Catalyst. I think, it's more Ubuntu-way decision, isn't it?
[http://www.mydailytechtips.com/2010/09/how-to-fix-fglrx-error-after-upgrading.html](http://www.mydailytechtips.com/2010/09/how-to-fix-fglrx-error-after-upgrading.html) - I can't understand, how this mess with reinstalling the same FGLRX can help. And a guy in the previous link has proved this decision doesn't help.
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) - this article has description for building DEB-packages from the latest driver downloaded from ATI web-site. The only nuance is this part HOW-TO was written for Maverick users. I don't understand whether I can use this article.
Thank you!

---

### Post by Anton K on 2011-02-27
I have found the solution.
This link helped me: [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide)

---

