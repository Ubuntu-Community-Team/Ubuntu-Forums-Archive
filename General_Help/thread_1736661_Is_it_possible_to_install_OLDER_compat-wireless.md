---
title: "Is it possible to install OLDER compat-wireless?"
date: 2011-04-22
forum: General Help
---

### Post by dennis1200 on 2011-04-22
I'm running 10.04 Ubuntu and am thinking about upgrading to 10.10 or 11.04 (or Mint equivalent). I've got an Intel 4965 driver and it seems like I'll lose 802.11n functionality with anything beyond kernel 2.6.34 (based on actual testing I've done, see [bug #630748]("https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/630748"). Is there a way to install older versions of just the wireless driver through something like compat-wireless? Or are those just for installing newer wireless drivers when running older kernels? I use N at home and it's nice, primarily for signal range. Thanks.

---

### Post by Yellow Pasque on 2011-04-22
It may be possible, or it may happen that the wireless-next source you build will expect kernel symbols that have been removed. wireless-next tarballs are archived: [http://www.orbit-lab.org/kernel/compat-wireless-2.6/](http://www.orbit-lab.org/kernel/compat-wireless-2.6/) so make sure that your version builds using the 11.04LiveCD (I recommend using a CD-RW or USB stick to avoid wasting a CD).

---

