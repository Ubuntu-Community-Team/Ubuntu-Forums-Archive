---
title: "Unable to mount/boot Windows Partition"
date: 2010-03-19
forum: General Help
---

### Post by drew212 on 2010-03-19
Upon trying to boot Windows I got through the GRUB startup selections and then i get stuck at a black screen displaying "Starting Up. . ." That would be no problem, I just boot ubuntu instead and mount the partition to access the programs I'm looking for. Now I get an interesting error message:

"Error mounting: mount exited with exit code 13: ntfs_mst_post_read_fixup: magic: 0x00150000  size: 4096  usa_ofs: 0  usa_count: 1040: Invalid argument
Actual VCN (0x15000011d92501) of index buffer is different from expected VCN (0x1).
Failed to mount '/dev/sda1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details."

I would run chkdsk in windows if I could, but that's my problem in the first place.

---

### Post by drew212 on 2010-03-20
Bump

---

### Post by drew212 on 2010-03-20
Anyone?

---

### Post by oldfred on 2010-03-20
Check disk from CD - WinXP recovery console - menu shown with example
[http://kb.wisc.edu/helpdesk/page.php?id=5097](http://kb.wisc.edu/helpdesk/page.php?id=5097)

You can also run check disk from a Vista or 7 repair disk.

---

