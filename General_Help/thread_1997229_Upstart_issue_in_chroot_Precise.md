---
title: "Upstart issue in chroot Precise"
date: 2012-06-04
forum: General Help
---

### Post by MaximumFish on 2012-06-04
Hi,

I'm running Ubuntu 12.04/Precise in a chroot on my Synology NAS and all's running well except, when updating packages with apt, I get errors like this:

Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused

It seems to be an [issue with Upstart](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/430224) in a chroot environment, and was supposed to have been fixed back in August last year. Indeed, chroot compatibility is [listed as a feature](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/TechnicalOverviewUpstart#Chroot_support) of 12.04, yet I'm still encountering the error!

I've implemented a workaround from the comments of the original bug, whereby you do the following:

```

dpkg-divert --local --rename --add /sbin/initctl
ln -s /bin/true /sbin/initctl

```

... and that works insofar as the apt upgrade now finishes "successfully", but surely I shouldn't need to do this in 12.04? And how does this workaround work exactly? Isn't it just tricking apt into thinking its command has succeeded, whereas actually it's done nothing? And if that's the case then I'd assume there'd be possible/probable side effects?

As it is I'm close to getting my ideal setup on this system but I'm being scuppered by this issue. The real problem is that I don't have enough knowledge of apt, upstart or chroot to know whether I should be concerned!

Any help or advice greatly appreciated. :)

Max

---

### Post by mtmx on 2012-11-09
Hi, just replying with a big thank you since I ran into this same issue in a precise chroot and your workaround was a perfect solution for me.

> **MaximumFish said:**
> 
I've implemented a workaround from the comments of the original bug, whereby you do the following:

```

dpkg-divert --local --rename --add /sbin/initctl
ln -s /bin/true /sbin/initctl

```

... and that works insofar as the apt upgrade now finishes "successfully", but surely I shouldn't need to do this in 12.04? And how does this workaround work exactly? Isn't it just tricking apt into thinking its command has succeeded, whereas actually it's done nothing? And if that's the case then I'd assume there'd be possible/probable side effects?


Yeah, that's it. Not apt but upstart. The link makes all commands that deal with starting and stopping system services to succeed unconditionally. If you **do** want to run a daemon in your chroot then you may have some issues to work out. If the chroot is just for testing or building, as in my use case, then there's no problem.

---

