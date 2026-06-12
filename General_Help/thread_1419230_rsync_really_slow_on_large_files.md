---
title: "rsync really slow on large files"
date: 2010-03-01
forum: General Help
---

### Post by alisdt on 2010-03-01
Hi,

I have Ubuntu on both my laptop and desktop machines, both are connected to the same network. I back up the laptop to the desktop by running the following on the laptop:

rsync -avv --stats /home/alisdt alisdt@xxx.xxx.xxx.xxx:/home/alisdt/laptop_backup

(with the IP address of the desktop instead of the many x, obviously).

Whenever rsync hits a large file (greater than a few MB), the network use rapidly drops to ~60KB/s (that's kilobytes not bits). When I copy the same file to the same place using scp, I get > 500KB/s throughout the transfer.

Things I've tried:

 * mounting the desktop home dir on the laptop using SSHFS -- a simple file copy is fast, rsync is still slow
 * ditto with NFS
 * rsync --whole-file option, in case the delta-transfer algorithm was choking on large files
 * rsync --inplace option
 * HPN-SSH ([http://www.psc.edu/networking/projects/hpn-ssh/](http://www.psc.edu/networking/projects/hpn-ssh/)) to enable dynamic window and unencrypted bulk transfer, just in case it was some ssh bottleneck

So, I think it's either an rsync application problem, or a network problem that is only affecting rsync. Any ideas, or other ideas of what I can try to debug? In case it's relevant, I'm using 9.04 on both machines. (A standing bug prevents me from upgrading the laptop, and I haven't bothered to upgrade the desktop).

I'd be grateful for anything you can suggest ....

---

### Post by alisdt on 2010-03-01
I should also note that there is no CPU bottleneck, while the transfer is underway CPU use on both laptop and desktop is < 20%.

---

### Post by alisdt on 2010-03-01
Just tried booting both machines using alpha release 3 of 10.04 (Lucid), and running rsync again.

Interestingly, the average transfer rate increases, it seems to be around 150KB/s. It is more variable than before, with highs around 500KB/s and serious lows (sometimes 0 for a few seconds). I note that the version of rsync is newer (3.0.7 on 10.04 vs. 3.0.5 on 9.04).

---

### Post by alisdt on 2010-03-01
I tried again (using the installed versions of Ubuntu, both 9.04), but I connected the laptop directly to the router using a cable rather than using wireless.

Using the rsync command line above, I get a consistent transfer rate of > 2.5MB/s. This would seem to suggest that there is a problem with wireless on the laptop. I get fair download speeds using the web and scp over wireless, so this problem seems to only affect rsync.

lspci reports the following for my wireless device:

02:02.0 Ethernet controller: Atheros Communications Inc. AR5212 802.11abg NIC (rev 01)

I presume that ath5k is the relevant kernel module, and indeed lsmod tells me that it is present.

---

