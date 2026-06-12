---
title: "Writing a bootsector.bin file to a USB sector 1"
date: 2011-11-04
forum: General Help
---

### Post by kammce on 2011-11-04
I was not sure if this was the appropriate forum area, so I choose this one.

I have seen many tutorials on how to do this in windows using downloadable programs, but I have no idea how to do this in Ubuntu. I assume it is the same in ever other variant of Linux but I just wanted to note that I am using Ubuntu 10.04LTS.

My main purpose for this is to write the 8086emu Micro-OS-Loader (Cylinder 0, head 0, Sector 1) and Micro-OS-Kernel (Cylinder 0, head 0, Sector 2) to a USB flash disk to test to see if it boots up or not. I could do this in Windows, but I want to know how to do this in Linux so I am not dependent on using Windows in order to write my Operating system's data on my USB.

If you need additional information on the system I am using, just ask and I will edit the first post.

Thank you for your help.

---

### Post by dcstar on 2011-11-04
> **kammce said:**
> I was not sure if this was the appropriate forum area, so I choose this one.

I have seen many tutorials on how to do this in windows using downloadable programs, but I have no idea how to do this in Ubuntu. I assume it is the same in ever other variant of Linux but I just wanted to note that I am using Ubuntu 10.04LTS.

My main purpose for this is to write the 8086emu Micro-OS-Loader (Cylinder 0, head 0, Sector 1) and Micro-OS-Kernel (Cylinder 0, head 0, Sector 2) to a USB flash disk to test to see if it boots up or not. I could do this in Windows, but I want to know how to do this in Linux so I am not dependent on using Windows in order to write my Operating system's data on my USB.

If you need additional information on the system I am using, just ask and I will edit the first post.

Thank you for your help.
This will write a bootsector (MBR) and leave the partition table:
```
sudo dd if=**whateverthefilenameis** of=/dev/sd**whateverthedriveis** bs=446 count=1
```
I will leave it to common-sense to substitute the appropriate data.

If you want to write the first 1024 bytes of one file to the first two sectors then:
```
sudo dd if=**whateverthefilenameis** of=/dev/sd**whateverthedriveis** bs=512 count=2
```

```
man dd
``` will supply details of the command.

---

### Post by kammce on 2011-11-06
Thank you very much for this!

---

