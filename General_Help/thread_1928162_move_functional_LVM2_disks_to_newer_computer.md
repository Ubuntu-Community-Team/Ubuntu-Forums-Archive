---
title: "move functional LVM2 disks to newer computer"
date: 2012-02-19
forum: General Help
---

### Post by bobwdn on 2012-02-19
I have an existing LVM2 (10.04LTS) server (multiple disks) running and would like to replace the old motherboard with a newer, faster MB. All referenced articles I can find discuss moving an LVM2 directory via 'vgexport' and 'vgimport' instructions. These articles reference a single directory, for example "/data" and how to 'vgexport' to "disconnect it" (if you will), move the drive to a new computer and 'vgimport' to reacquire the volume on the newer computer. 

I have a /boot partition that is NOT part of the LVM2 volume group. All other directories (/, /var, /usr, etc.) are spread across my logical volume group called 'vol_grp_one'. Some years back, I followed an article:```
http://www.linuxbsdos.com/2008/11/11/lvm-configuration-in-ubuntu-810/?upm_export=doc
``` That article was based on Ubuntu 8.10. It worked fine with my 10.04LTS.

Basically, the entire directory file system is on the LVM2 volume except the /boot partition.

If I am replacing the existing motherboard with a newer faster motherboard(MB). And I maintain the same disk assignment order they were attached to the old MB (make sure sda1 remains sda1 on the newer MB and sdb1, sdc1, etc., remains sdb1, sdc1 on the newer MB.) Will it boot and NOT damage the LVM2 volume allowing the computer to boot and start properly? Has anyone got any experience in moving multiple LVM2 hard drives to a newer MB like this?

---

