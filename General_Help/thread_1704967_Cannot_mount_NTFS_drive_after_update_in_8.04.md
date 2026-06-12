---
title: "Cannot mount NTFS drive after update in 8.04"
date: 2011-03-11
forum: General Help
---

### Post by ordealbyfire83 on 2011-03-11
Hello, I can no longer access my external USB hard drive after applying routine updates this morning. It is a WD "My Passport" drive, 500 GB with the standard formatting setup. As far as I can tell there are no errors on it. Upon plugging it in I see a pop-up box "Unable to mount the volume 'My Passport'" and it provides no further information under "Details." If I try mounting from the command line, e.g. mount -t ntfs-3g /dev/sdb1 /media/sdb1 or similar, no errors appear but when I do ls on the directory it comes up blank. Also then if I try to unmount it, it tells me the drive isn't mounted. This drive mounts fine on another computer running Fedora (and all the data on it is readable). I'm guessing there is a bug in one of the updates--here is what updates I applied. Thanks.

Commit Log for Fri Mar 11 18:09:25 2011


Upgraded the following packages:
avahi-autoipd (0.6.22-2ubuntu4.2) to 0.6.22-2ubuntu4.3
avahi-daemon (0.6.22-2ubuntu4.2) to 0.6.22-2ubuntu4.3
firefox (3.6.14+build3+nobinonly-0ubuntu0.8.04.1) to 3.6.15+build1+nobinonly-0ubuntu0.8.04.1
firefox-3.0 (3.6.14+build3+nobinonly-0ubuntu0.8.04.1) to 3.6.15+build1+nobinonly-0ubuntu0.8.04.1
firefox-3.0-gnome-support (3.6.14+build3+nobinonly-0ubuntu0.8.04.1) to 3.6.15+build1+nobinonly-0ubuntu0.8.04.1
firefox-branding (3.6.14+build3+nobinonly-0ubuntu0.8.04.1) to 3.6.15+build1+nobinonly-0ubuntu0.8.04.1
firefox-gnome-support (3.6.14+build3+nobinonly-0ubuntu0.8.04.1) to 3.6.15+build1+nobinonly-0ubuntu0.8.04.1
fuse-utils (2.7.2-1ubuntu2.2) to 2.7.2-1ubuntu2.3
libavahi-client-dev (0.6.22-2ubuntu4.2) to 0.6.22-2ubuntu4.3
libavahi-client3 (0.6.22-2ubuntu4.2) to 0.6.22-2ubuntu4.3
libavahi-common-data (0.6.22-2ubuntu4.2) to 0.6.22-2ubuntu4.3
libavahi-common-dev (0.6.22-2ubuntu4.2) to 0.6.22-2ubuntu4.3
libavahi-common3 (0.6.22-2ubuntu4.2) to 0.6.22-2ubuntu4.3
libavahi-compat-libdnssd1 (0.6.22-2ubuntu4.2) to 0.6.22-2ubuntu4.3
libavahi-core5 (0.6.22-2ubuntu4.2) to 0.6.22-2ubuntu4.3
libavahi-glib1 (0.6.22-2ubuntu4.2) to 0.6.22-2ubuntu4.3
libavahi-qt3-1 (0.6.22-2ubuntu4.2) to 0.6.22-2ubuntu4.3
libavahi-ui0 (0.6.22-2ubuntu4.2) to 0.6.22-2ubuntu4.3
libfuse2 (2.7.2-1ubuntu2.2) to 2.7.2-1ubuntu2.3
libpam-smbpass (3.0.28a-1ubuntu4.13) to 3.0.28a-1ubuntu4.14
libpango1.0-0 (1.20.5-0ubuntu1.1) to 1.20.5-0ubuntu1.2
libpango1.0-common (1.20.5-0ubuntu1.1) to 1.20.5-0ubuntu1.2
libpango1.0-dev (1.20.5-0ubuntu1.1) to 1.20.5-0ubuntu1.2
libsmbclient (3.0.28a-1ubuntu4.13) to 3.0.28a-1ubuntu4.14
libtiff4 (3.8.2-7ubuntu3.6) to 3.8.2-7ubuntu3.7
samba (3.0.28a-1ubuntu4.13) to 3.0.28a-1ubuntu4.14
samba-common (3.0.28a-1ubuntu4.13) to 3.0.28a-1ubuntu4.14
smbclient (3.0.28a-1ubuntu4.13) to 3.0.28a-1ubuntu4.14
tzdata (2011b~repack-0ubuntu0.8.04) to 2011c~repack-0ubuntu0.8.04
winbind (3.0.28a-1ubuntu4.13) to 3.0.28a-1ubuntu4.14

---

### Post by coffeecat on 2011-03-11
I wonder if fuse-utils and/or libfuse2 may be the problem. They are needed for the ntfs-3g driver to work, but have you checked with external drives formatted with different filesystems? Can you automount a FAT32-formatted drive?

By the way, if you are running the desktop version of 8.04, were you aware that it is due to go end-of-life in about 5-6 weeks? You might want to think about when and how you do a version upgrade.

---

### Post by ordealbyfire83 on 2011-03-11
Thanks for the reply. You might be on to something with fuse, because all along I used to see an entry in the File Systems tab in the System Monitor for fuse which had the identical Total/Free/Available/Used info as my ext3 partition (sda2). This entry is now gone. Flash drives seem to automount just fine though.

I suppose when Hardy reaches end-of-life I will upgrade to Lucid. Although if any of these updates got pushed to Lucid this issue might extend beyond Hardy.

---

### Post by ordealbyfire83 on 2011-03-11
Yep sure enough. I removed libfuse2 and fuse-utils, which also removed gvfs-fuse, ntfs-3g, ntfsprogs, and sshfs. Every month or so I move all my files aside, shrink the partition as small as it'll go and dd it somewhere else to have a backup, so I chroot'ed in there and did dpkg-repack for libfuse2 and fuse-utils to repackage the old versions. I installed those, and reinstalled gvfs-fuse, ntfs-3g, ntfsprogs, and sshfs and voila! Everything works fine.

Although, one thing I did notice was that the initrd was repackaged during this process. However it only repackaged the most recent version (2.6.24-28) and not the one that I'm using (2.6.24-25). This might have been part of the problem too.

---

