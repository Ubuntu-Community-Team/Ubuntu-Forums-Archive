---
title: "Can't boot after windows install"
date: 2011-08-28
forum: General Help
---

### Post by Lockheed on 2011-08-28
No, it's not this typical boring question again.

I had arch installed on sda2 with boot partition on sda3. I installed Windows 7 on sda4 and after installation, I restored grub.

Except now grub complaints "Error 15: file not found" when trying to boot linux. This does not make any sense.

Here's some details (all linux partitions = ext4:
```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
240 heads, 63 sectors/track, 41345 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x00085baa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       37086   280366348+  83  Linux
/dev/sda2           37086       39306    16779892+  83  Linux
/dev/sda3           39306       39314       64260   83  Linux
/dev/sda4   *       39314       41346    15358976    7  HPFS/NTFS
```
sda1 is a data partition.

```
# (0) Arch Linux
title  Arch
root   (hd0,1)
kernel /vmlinuz26 root=/dev/sda3 resume=/dev/sda3 resume_offset=1748992 ro quiet vga=785 sr0=ide-scsi
initrd /kernel26.img
```
Even if I change "root" to  (hd0,2) (which is wrong) the boot process goes further but stops after not being able to find /sbin/... <something>


What is wrong?

---

### Post by oldfred on 2011-08-28
If boot partition is sda3 the set root  (which in grub is boot partition) has to be hd0,2 in grub legacy. 
And the kernel line should be sda2 as that is where / (root) is. Separate /boots and old grub are now so confusing.

If you want all the details:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by Lockheed on 2011-08-28
Apparently, windows decided it would be a good idea to change order of partitions. I realised it eventually, and fixed it.
Thanks

---

