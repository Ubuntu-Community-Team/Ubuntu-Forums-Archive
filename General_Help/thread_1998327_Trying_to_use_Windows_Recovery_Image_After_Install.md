---
title: "Trying to use Windows Recovery Image After Installing Ubuntu Fails"
date: 2012-06-06
forum: General Help
---

### Post by dano2 on 2012-06-06
1) I had dual boot working with Windows 7 and Ubuntu 10.04LTS.

2) I successfully ran DBAN on my whole system. Then ran my 6-disk Windows Recovery/Restore image to successfully bring it back to a Windows 7 only system.

3) Then using the Live CD I successfully installed Ubuntu 10.04 again, dedicating the whole system to Ubuntu (no more Windows).

4) Now I want to dual boot again (starting with installing Windows 7). So again I ran my 6-disk Windows Recovery/Restore image which returned "Successfully restored the disk from the ASUS Recovery DVD".

5) But now, when trying to boot, I only get "error: unknown filesystem. grub rescue>". An "ls" returns "(hd0) (hd0,2) (hd0,1)"

I don't know what any of this means. From what I've read, I may need to create a primary partition in ntfs or fat format to place it's boot code, but I don't know how. Any suggestions? I'm in Ubuntu Live Test mode now.

"sudo fdisk -l" returns...

[PHP]
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c1d5a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3264    26214400    c  W95 FAT32 (LBA)
/dev/sda2            3264       27585   195354624    7  HPFS/NTFS
/dev/sda3           59489       60802    10543105    5  Extended
ubuntu@ubuntu:~$
[/PHP]

---

