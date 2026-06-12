---
title: "Is NTFS support stable?"
date: 2011-11-11
forum: General Help
---

### Post by JonUK76 on 2011-11-11
I dual boot between Windows 7 and Ubuntu 11.10 64bit.  Yesterday, I was using Ubuntu and decided to move some video files from the Windows partition to an external drive (the external drive is also NTFS formatted).  I've done some file moving before (perhaps not quite so large files) and not had any problems.  All seemed to go well at least initially.  Files appeared to have copied across and were accessible from within Ubuntu.

However later on, I logged out of Ubuntu (cleanly) and re-booted into Windows 7 and noticed the folder on the external drive I'd moved the files into had disappeared.  None of the files were visible.  Also Windows was slower (than usual!).  I immediately shut down and re-booted into System Recovery Console and ran CHKDSK.  Result - corrupted MFT on both the external drive and the main Windows drive.  Luckily I was able to fix it, but it took many hours of scanning and a lot of head scratching.

In short my question is, is NTFS support in Ubuntu considered stable and reliable?  Or should I treat it as "experimental" still?  I'm very wary of using it following this incident, but what are your thoughts, and any idea why this happened this time?

Thanks

---

### Post by WorMzy on 2011-11-11
I've been using it for several years without incident, so yes, I would say it is stable.

---

### Post by Bucky Ball on 2011-11-11
NTFS very stable. There could be another explanation. How could what you did possibly effect your Windows partition? You weren't writing to it. Perhaps it has something to do with what Windows does to them when you store them on a Windows partition (where Windows is installed, that is). Interesting. Some brain might see the problem immediately ... ;)

Are you using ntfs-3g in Ubuntu?

---

### Post by JonUK76 on 2011-11-11
> **Bucky Ball said:**
> NTFS very stable. There could be another explanation. How could what you did possibly effect your Windows partition? You weren't writing to it.

I would say it was writing to it, I think?  I was moving files from it, not simply copying, therefore I assume (without detailed knowledge of how NTFS works) deleting files would result in the MFT being written to, to reflect that there are now less files in the partition.

> Are you using ntfs-3g in Ubuntu?

Not intentionally.  To clarify, I'm using the support built into Ubuntu by default.  If that is not NTFS-3G, I'll remove it from the "tags" to avoid confusion.  I thought I'd read somewhere Linux support for NTFS was through NTFS-3G but perhaps that's dated or wrong?

Thanks for the replies :)

---

### Post by alex2399 on 2011-11-11
The package ntfs-3g was not installed by default on my machine, only ntfsprogs. The package ntfs-3g is needed to actually write to NTFS partitions AFAIK, ntfsprogs can only read.

---

### Post by JonUK76 on 2011-11-11
Ah I see.  Apparently ntfsprogs and NTFS-3G were merged into one as of April this year - [http://www.tuxera.com/open-source/release-ntfs-3g-ntfsprogs-2011-4-12/](http://www.tuxera.com/open-source/release-ntfs-3g-ntfsprogs-2011-4-12/)

Ubuntu 11.10 (and IIRC, other recent versions I've used) can definitely write to NTFS file systems by default anyway, without installing any additional packages.

---

### Post by alex2399 on 2011-11-11
The ntfsprogs version is still the old not merged one and if you look in the Software Center, Launchpad or via apt-get you will see it has no proper write support, only ntfs-3g has whatever version it may be.

---

### Post by oldfred on 2011-11-11
Were you hibernated in Windows when you moved the files? That is often one of the major causes of issues as the hiberfile is then corrupted by some action in  anther system whether Ubuntu or another install of Windows.

---

### Post by sgage on 2011-11-11
> **WorMzy said:**
> I've been using it for several years without incident, so yes, I would say it is stable.

Ditto. In several years of using NTFS, I've never had a problem.

---

### Post by coffeecat on 2011-11-11
> **alex2399 said:**
> The package ntfs-3g was not installed by default on my machine, only ntfsprogs. The package ntfs-3g is needed to actually write to NTFS partitions AFAIK, ntfsprogs can only read.

> **alex2399 said:**
> The ntfsprogs version is still the old not merged one and if you look in the Software Center, Launchpad or via apt-get you will see it has no proper write support, only ntfs-3g has whatever version it may be.

Point of information. ntfsprogs is/was a suite of utilities for working with NTFS filesystems, and those utilities have now been merged into the ntfs-3g driver package (as JonUK76 says) as from the version that comes with 11.10. Consequently, in 11.10, the ntfsprogs package conflicts with ntfs-3g. The package ntfs-3g **is** installed by default in 11.10, as it has in recent Ubuntu versions, but some people are accidentally allowing it to be uninstalled by installing ntfsprogs, thinking they need ntfsprogs - which they don't.

Sorry to pick you up on this point, but there is some confusion about the whole ntfs-3g/ntfsprogs situation in 11.10, and I seem to have spent a lot of time in this forum recently telling people to **re**-install ntfs-3g after it has gone awol - probably because of ntfsprogs being installed. :)

**EDIT**: just to add. If you remove ntfs-3g, you lose write capability (to NTFS) but retain read. As far as I can make out, this is because the system falls back to the old read-only ntfs kernel module.

---

### Post by JonUK76 on 2011-11-11
> **alex2399 said:**
> The ntfsprogs version is still the old not merged one and if you look in the Software Center, Launchpad or via apt-get you will see it has no proper write support, only ntfs-3g has whatever version it may be.

Just checked and I have "read/write NTFS driver for FUSE - ntfs-3g 1:2011.4.12AR.4-2ubuntu3" installed.  So that's not there by default then?  I didn't manually add it. Perhaps the Ubuntu installer detected I had NTFS drives attached and installed it, is that possible?  EDIT Just saw coffeecat's reply that clears that issue up :) Thanks

> **oldfred said:**
> Were you hibernated in Windows when you moved the files? That is often one of the major causes of issues as the hiberfile is then corrupted by some action in  anther system whether Ubuntu or another install of Windows.

Thanks for the suggestion.  No I don't have hibernation enabled in Windows - it's caused issues in the past for me.

So the majority view seems to be that it works correctly then?  Like I said, I haven't had a problem before, but trying to work out what happened this time.  Maybe for whatever reason it didn't dismount the volumes cleanly when I shut down Ubuntu?  Would there be any way to find out?

---

### Post by alex2399 on 2011-11-12
> **coffeecat said:**
> Point of information. ntfsprogs is/was a suite of utilities for working with NTFS filesystems, and those utilities have now been merged into the ntfs-3g driver package (as JonUK76 says) as from the version that comes with 11.10. Consequently, in 11.10, the ntfsprogs package conflicts with ntfs-3g. The package ntfs-3g **is** installed by default in 11.10, as it has in recent Ubuntu versions, but some people are accidentally allowing it to be uninstalled by installing ntfsprogs, thinking they need ntfsprogs - which they don't.

Sorry to pick you up on this point, but there is some confusion about the whole ntfs-3g/ntfsprogs situation in 11.10, and I seem to have spent a lot of time in this forum recently telling people to **re**-install ntfs-3g after it has gone awol - probably because of ntfsprogs being installed. :)

**EDIT**: just to add. If you remove ntfs-3g, you lose write capability (to NTFS) but retain read. As far as I can make out, this is because the system falls back to the old read-only ntfs kernel module.

Just checked the install log and you are right, it is installed by default but it got deleted from my machine. I suspect it was during the installation of Gparted and selecting the Add-on ntfsprogs which seemed necessary for doing "neat things in NTFS" partitions.

---

### Post by coffeecat on 2011-11-12
> **alex2399 said:**
> I suspect it was during the installation of Gparted and selecting the Add-on ntfsprogs which seemed necessary for doing "neat things in NTFS" partitions.

Thanks for mentioning that. Yes, that's probably another reason why people are trying to install ntfsprogs. In Gparted, View -> File System Support lists ntfsprogs next to ntfs under "Required Software" which is misleading.

But it gets worse - or more bizarre. If you look at gparted's list of dependencies in Synaptic, ntfsprogs is "Suggests", which again is misleading, but it also lists "gparted" as "Conflicts"! Gparted conflicts with Gparted? :-k

---

