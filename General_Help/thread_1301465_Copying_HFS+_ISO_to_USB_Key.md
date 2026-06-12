---
title: "Copying HFS+ ISO to USB Key"
date: 2009-10-26
forum: General Help
---

### Post by patryk77 on 2009-10-26
Hey,

I have an HFS+ formatted ISO file, that I need to put on a bootable USB key.

I tried ```
dd if=file.iso of=/dev/sdc
``` but it does not boot (not surprising) and fdisk -l gives me > Disk /dev/sdc doesn't contain a valid partition table.

dd printed out statistics and exited without errors.

```
sudo mount -t hfsplus -o loop file.iso /mnt/iso/
``` mounts it successfully and allows me to see the contents, but I need to be able to boot from it on a netbook with no DVD-ROM.

Any suggestions? Thanks

---

### Post by patryk77 on 2009-10-26
Actually, it seems to be able to mount the disk, and I can see the files.

However, fdisk -l still claims there is no valid partition table and I cannot set the bootable flag as it sees no partitions.

Edit: Parted will probably help.

This is what it says about my USB key:
> (parted) print                                                            
No Implementation: Partition 3 isn't aligned to cylinder boundaries.  This is still unsupported.

And this is the mounted ISO:```

(parted) print                                                            
Model: Unknown (unknown)
Disk /dev/loop0: 2831MB
Sector size (logical/physical): 512B/512B
Partition Table: mac

Number  Start  End     Size    File system  Name          Flags
 1      512B   32.8kB  32.3kB               Apple              
 3      557kB  2831MB  2831MB  hfs+         
```

---

