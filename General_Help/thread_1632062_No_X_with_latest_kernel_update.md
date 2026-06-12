---
title: "No X with latest kernel update"
date: 2010-11-27
forum: General Help
---

### Post by bobnutfield on 2010-11-27
Hello Everyone

This is old P4 laptop, Intel845G graphics (which I know is very troublesome).

However, it works fine with the 2.6.35.22, but the update to 2.6.35.23 kills X during the boot process.  Everything else works fine.

Anyone else experiencing any difficulty with X and this kernel update?

Thanks for any replies.

Bob

---

### Post by andrewthomas on 2010-11-27
Maybe there was a problem with building the initramfs.

Try to update the images from the console.

```
sudo update-initramfs -u -k all
```

---

### Post by Mouloud on 2010-11-30
I have the same problem with my desktop computer with nvidia graphics. When I start with the new .23 kernel, x says that I don't have anything configured. .22 starts well as usual.
The initramfs command does not have any effect on the problem.

---

### Post by ptn107 on 2010-11-30
Running 2.6.35-23.41 here and both the proprietary (v260.19.21) and nouveau (v1:0.0.16+git20100805+b96170a-0ubuntu1) drivers work fine on 64-bit.

---

