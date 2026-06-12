---
title: "Anyone else get the Update to 2.6.38.10 that breaks FGLRX?"
date: 2011-06-06
forum: General Help
---

### Post by emarkay on 2011-06-06
10.04 LTS, 32 Intel
Maybe it's a fluke, maybe an error, but I have no graphic acceleration.

I noticed a bug filed today that may have something to do with it?
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/793442](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/793442)

Will reboot into older kernel via GRUB 2 and hope things go back to normal.

---

### Post by TBABill on 2011-06-06
That link goes to a bug for 11.10 for kernel 2.6.39-3.10. However, another user has posted a non-booting upgraded kernel just like what you posted, found [http://ubuntuforums.org/showthread.php?t=1776550](http://ubuntuforums.org/showthread.php?t=1776550)

---

### Post by emarkay on 2011-06-06
OK, got it - here's the scoop from the source: 


"
Hello Ubuntu developers,

Today we released another round of Linux kernel updates to
lucid/maverick/natty-proposed. However, the proposed natty update
(2.6.38 based kernel) was accidentally copied to lucid-proposed and
maverick-proposed, and thus had been on the master archive.ubuntu.com
between 09:00 and 14:00 UTC.

That means, if you have proposed updates enabled on your 10.04 LTS
(lucid) or 10.10 (maverick) Ubuntu installation, and did a system
upgrade during that time, it might have pulled in the 2.6.38 kernel.

To check this, please run

  dpkg -l linux* | grep '^ii.*2.6.38'

If you have any results, please first run another system upgrade,
which will again pull in the 2.6.32 (lucid) or 2.6.35 (maverick)
kernels, and then remove the wrong kernel packages with

  sudo apt-get purge `dpkg -l linux* | grep '^ii.*2.6.38' | awk '{print $2}'`

I fixed the script that handles the proposed kernel packages now, so
this won't happen again.

I sincerely apologize for any inconvenience that this caused!"


[https://lists.ubuntu.com/archives/ubuntu-devel-announce/2011-June/000854.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2011-June/000854.html)

---

