---
title: "recover eCryptfs encrypted files with ext3grep"
date: 2011-01-03
forum: General Help
---

### Post by COKEDUDE on 2011-01-03
Is it possible to recover eCryptfs encrypted files with ext3grep? I keep getting really weird messages at the end when I try to recover eCryptfs encrypted files. It also aborts at the end.

```
Extended directory at 6604582 belongs to inode 1204620 (from journal).
Extended directory at 6604583 belongs to inode 1204620 (from journal).
Extended directory at 6809341 belongs to inode 1204620 (from journal).
Extended directory at 6809342 belongs to inode 1204620 (from journal).
Extended directory at 6842770 belongs to inode 1229066 (from 23 linked directories).
Extended directory at 6996984 belongs to inode 1229066 (from 22 linked directories).
Extended directory at 7030791 belongs to inode 1753090 (from 2 linked directories).
Extended directory at 7045639 belongs to inode 1753090 (from 2 linked directories).
Extended directory at 7356485 belongs to inode 1835017 (from journal).
Extended directory at 7356486 belongs to inode 1835017 (from journal).
Extended directory at 7356487 belongs to inode 1835017 (from journal).
Extended directory at 7356488 belongs to inode 1835017 (from journal).
Cannot find a directory block for inode 1482836.
Cannot find a directory block for inode 1753197.
Cannot find a directory block for inode 1589259.
Cannot find a directory block for inode 1441793.
Adding extended directory block(s) for directory ".ecryptfs/bob/.Private".
Adding extended directory block(s) for directory ".ecryptfs/bob/.Private/ECRYPTFS_FNEK_ENCRYPTED.FWZoKWTBp1k8MURZxkpAZpqlxC12-iwYH.gB0QakULbN7UG92krlhqNKhU--/ECRYPTFS_FNEK_ENCRYPTED.FWZoKWTBp1k8MURZxkpAZpqlxC12-iwYH.gBp-qFGWEDQR0BTIlYvwu-Uk--/ECRYPTFS_FNEK_ENCRYPTED.FWZoKWTBp1k8MURZxkpAZpqlxC12-iwYH.gBGw9KV6Pxnm1x5d8Lg1jLdk--/ECRYPTFS_FNEK_ENCRYPTED.FWZoKWTBp1k8MURZxkpAZpqlxC12-iwYH.gBfV9CYnt7htg5mvbwBTAHY---/ECRYPTFS_FNEK_ENCRYPTED.FWZoKWTBp1k8MURZxkpAZpqlxC12-iwYH.gBSk88AdWHDVEhYej6o0PcPk--".
ext3grep: init_directories.cc:506: void init_directories(): Assertion `parent.dirname(false) == dir_iter->first' failed.
Aborted
```

---

