---
title: "EXT4 file system getting remounted a bunch, why?"
date: 2010-12-19
forum: General Help
---

### Post by Docteh on 2010-12-19
I just installed ubuntu on to a brand new samsung N310 series netbook, I opted for ext4 as I figure it should be stable, but awhile ago the laptop shut off with no visible reason, when I restarted I noticed that this is happening. What gives?

[  202.405576] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[  243.500906] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[  303.782887] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[  405.227832] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[  511.181704] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[  612.592685] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[  714.002341] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[  820.034600] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[  921.379744] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[ 1027.411223] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[ 1128.799389] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[ 1239.430946] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[ 1354.628611] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[ 1479.158479] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[ 1608.210717] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[ 1751.081002] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[ 1903.198066] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[ 2073.744198] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[ 2258.078145] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[ 2456.242023] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[ 2682.092638] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[ 2940.239318] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[ 3230.581456] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[ 3567.005977] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[ 3954.180746] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[ 4428.921716] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[ 4862.133954] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0

---

### Post by Vermind on 2011-02-25
Hi,
I am seeing this on Maverick as well:
```
[   29.853269] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,commit=1200,commit=0
```
At some point, mount starts to show commit=1200,commit=0 as well, so there are TWO values for the commit option!?!?
I'd really like to keep it commit=1200. I believe this only happens when filesystems are remounted, and may have something to do with power management. I think plugging in/unplugging this laptop makes this message show more frequently in dmesg.

A workaround from [http://ubuntuforums.org/showthread.php?t=1670082](http://ubuntuforums.org/showthread.php?t=1670082)
is ```
sudo mountall
```

Edit: Found a likely culprit:
in /usr/lib/pm-utils/power.d/journal-commit,
the commit values are set based on if we are on AC or battery. I can delete the file, but that will bring it back when pm-utils is next updated. I can dpkg-divert the file, but it would have to be diverted out of the pm-utils/something.d hierarchy so it is not run. Any cleaner solutions?

---

### Post by vangop on 2011-07-15
Hi!
I have the same behavior in 10.10 x64, but also add to this increased network lag.
I ping lan pc normally 1-2ms on AC, when on battery the ping is 100-200.
Switching back AC again makes it 1-2 ms. 
I changed the commit to be the same in both cases in the script, but the ping still changes.
Any idea what another pm-util thing can cause it?

---

### Post by vangop on 2011-07-21
Filed a bug for it. [https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/811552]("https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/811552")
The solution now is
```
$ sudo chmod -x /usr/lib/pm-utils/power.d/wireless
```

---

