---
title: "Unable to mount partition in Ubuntu Natty"
date: 2011-10-01
forum: General Help
---

### Post by sweetchuggagun on 2011-10-01
Hello people! I moved to Ubuntu for a few months after being for a long time an Windows user. I am a beginner when it comes to linux, my only knowledge about how things go in Ubuntu are from what I had in my little experience.

So, this is my problem. I have an 80GB hard disk split in 3 partions - 9.5, 14,3 and 50 GB(ubuntu instalation is on the second) and a swap area.
While I was moving some pictures from a USB flash drive into the 50GB partition ubuntu crashed and since then I am unable to get into this partition(which contains docs and photos that I need :(( ). 
This is the messa ge I get on I click on it "Unable to mount 54 GB Filesystem"
Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sda5': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

I run a sudo fdisk -l
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x71a28c9f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1246    10000000    b  W95 FAT32
/dev/sda2            3106        9728    53192449    f  W95 Ext'd (LBA)
/dev/sda3            1246        3106    14945280   83  Linux
/dev/sda5            3200        9728    52444161    7  HPFS/NTFS
/dev/sda6            3106        3199      747520   82  Linux swap / Solaris

Partition table entries are not in disk order

Other threads suggested to create new folders in "media" for each partitions than assign new mounting points to those points using mountmanager and to modify the /etc/fstab(which was difficult for me to understand), but I don't know if this is safe(the pictures and the documents are really important). 

Do you have any advice for mounting safely the partition without data loss? Thank you!

---

### Post by prodigy_ on 2011-10-01
> **sweetchuggagun said:**
> Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
Use Windows **chkdsk** tool on this partition to fix the MFT. If you don't have Windows, try [TestDisk](http://www.cgsecurity.org/wiki/TestDisk).

---

### Post by sweetchuggagun on 2011-10-01
The problem is that Ubuntu is the only OS on my computer.

---

### Post by prodigy_ on 2011-10-01
> **sweetchuggagun said:**
> The problem is that Ubuntu is the only OS on my computer.
If it's not a hardware issue, TestDisk should help. Try it.

Also, if you've decided to ditch Windows completely, there's no reason for you to use FAT/NTFS anymore. Think about converting to a native Linux filesystem like ext4. :)

---

### Post by sweetchuggagun on 2011-10-01
Well can you give me some step-by-step instruction with TestDisk? How do I mount the 50GB partition?

---

### Post by sweetchuggagun on 2011-10-02
I managed to recover all data with TestDisk but now I'm stuck with mounting the 50GB volume. Do you have any suggestion about how can I do it? I tried with Disk Utility and Mountmanager but it didn't work...

---

### Post by sweetchuggagun on 2011-10-02
In the end I decided to format the volume. Anyway, thanks for the TestDisk utility.

---

