---
title: "Ubuntu 8.10 + SSD for build time optimization?"
date: 2010-05-24
forum: General Help
---

### Post by Homncruse on 2010-05-24
I'm evaluating options for improving build times for developers at my workplace. I'm currently setup with an i7 920 machine with 4GB RAM. This alone has been a significant improvement over my old setup (don't ask...). In any event, I'm now evaluating the Intel x25 SSD here: [http://www.newegg.com/Product/Product.aspx?Item=N82E16820167016](http://www.newegg.com/Product/Product.aspx?Item=N82E16820167016)

When I run identical builds both from the SSD and from the HDD, I get fairly identical build times (+/- 5% improvement). To be honest, I expected much more noticeable results, so I suspect maybe I'm not set up correctly.

The OS is still running on the HDD. I have a single ext3 partition on the SSD with default mounting options. I'm running Ubuntu 8.10 with kernel 2.6.27-17 -- and no, I can't upgrade the kernel due to stupid proprietary ATI drivers for our video chipset (open-source driver isn't sufficient, and ATI stopped supporting the chipset - but we need to use this chipset to reproduce the hardware environment for our embedded system).

Is this a battle even worth fighting? I've read in various places that SSD TRIM support is only present in the latest kernels under a specific filesystem. Am I going to destroy the SSD's performance by using it with an old kernel?

---

