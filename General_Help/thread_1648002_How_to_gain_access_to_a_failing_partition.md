---
title: "How to gain access to a failing partition"
date: 2010-12-18
forum: General Help
---

### Post by okayneil on 2010-12-18
Hey everyone, 

I'm working with a laptop that will not boot into windows (the sole partition)

I'm working on a laptop that recognises that a windows partition is present in ubuntu live CD but will not mount it so that I can gain access to the system to recover files. 

I get this error:

```
Failed to mount: '/dev/sda2': input/output error
```

What I want to know is how to force mount the partition so that I can gain access or any other method that will allow me to recover those files. 

Thanks, 

Neil

---

### Post by Verbeck on 2010-12-18
try
```
sudo mount /dev/sda2 /mnt -o force
```

---

### Post by okayneil on 2010-12-18
> **Verbeck said:**
> try
```
sudo mount /dev/sda2 /mnt -o force
```

Hey, 

I get the same error and the partition will not mount.

---

### Post by okayneil on 2010-12-18
Bump, i need some major help here guys.

---

### Post by oldfred on 2010-12-18
Have you tried running chkdsk from a windows CD? Ubuntu & gparted often will not mount a NTFS partition if chkdsk flag is set. You have to run chkdsk until there are no errors as it does not fix them all on one pass.

Sometimes windows chkdsk, does not work and this may.
If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

---

