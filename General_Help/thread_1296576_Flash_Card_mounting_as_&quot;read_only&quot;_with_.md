---
title: "Flash Card mounting as &quot;read only&quot; with errors"
date: 2009-10-20
forum: General Help
---

### Post by beastrace91 on 2009-10-20
Hey There,

So not quiet sure what I did to my flash card but it not longer auto mounts, upon trying to manually mount it it suggested I run a **dmesg | tail** to get debug information - but now I am not quiet sure how to resolve my issue using said information.

Here is the output from terminal: ```
jeff@eeetop:~$ sudo mount -t ext3 /dev/sdb1 /mnt/cardreader
mount: block device /dev/sdb1 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

jeff@eeetop:~$ dmesg | tail
[   21.845256] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   26.278435] EXT3-fs: INFO: recovery required on readonly filesystem.
[   26.278447] EXT3-fs: write access unavailable, cannot proceed.
[   32.256113] wlan0: no IPv6 routers present
[  292.085000] EXT3-fs: INFO: recovery required on readonly filesystem.
[  292.085019] EXT3-fs: write access unavailable, cannot proceed.
[  468.333224] ath5k phy0: noise floor calibration timeout (2432MHz)
[  621.333646] ath5k phy0: noise floor calibration timeout (2432MHz)
[  679.830647] EXT3-fs: INFO: recovery required on readonly filesystem.
[  679.830658] EXT3-fs: write access unavailable, cannot proceed.

```

How can I fix the issue so I can use the disc again (with out loosing the data...) gParted shows the drive with a ! in front of it when I look at it. Any help would be awesome.

Thanks,
~Jeff

---

