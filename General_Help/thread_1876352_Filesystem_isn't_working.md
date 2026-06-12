---
title: "Filesystem isn't working"
date: 2011-11-06
forum: General Help
---

### Post by leilei1 on 2011-11-06
So I accidentally screwed up the file system on my external hard drive which had two partitions on it. Now when I open up one partition it's completely empty and when I try to open the other i get this message:

Error mounting: mount exited with exit code 13: ntfs_mst_post_read_fixup: magic: 0x00000000  size: 4096  usa_ofs: 0  usa_count: 65535: Invalid argument
Index buffer (VCN 0x0) of directory inode 0x5 has a size (24) differing from the directory specified size (4096).
Failed to mount '/dev/sdd2': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

I know my files are still on the drive because when I check the available disk space it shows about 150 gb being used up so I'm guessing those are my files. So what I'm guessing is that I should run "chkdsk /f" in windows but I'm not sure because the error message is talking about a RAID which I am not doing so I'm a bit confused.

---

### Post by shakabra on 2011-11-06
[SIZE="3"][COLOR="Red"]**[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)**[/COLOR][/SIZE]

---

