---
title: "Mounting Ubuntu Partition to Windows"
date: 2011-03-21
forum: General Help
---

### Post by xTLx on 2011-03-21
I've dual-booted my laptop and mounted the Windows 7 Partition of my hard-drive to my Ubuntu partition, which is great, but I'm wondering how to also do the opposite. I want to mount the Ubuntu partition to my Windows 7 one and I'm unsure of how to do so. Help? :confused:

---

### Post by Script Warlock on 2011-03-21
possibly with ext2read

---

### Post by xTLx on 2011-03-21
So I downloaded and tried using the program in Windows 7, but it keeps telling me it can't read the disk and in the programs log it says "[I]Error Opening \\.\PhysicalDrive0. Error Code 5
No of disks 0[/I]"

Any suggestions? Should I try another program?

---

### Post by vanadium on 2011-03-21
You don't want to do that. Keep your data on the Windows partition, and you can access them from both Windows and Ubuntu.

---

### Post by Mark Phelps on 2011-03-21
> **xTLx said:**
> I've dual-booted my laptop and mounted the Windows 7 Partition of my hard-drive to my Ubuntu partition, which is great ...

Not really ... doing this with the Win7 OS partition runs the risk of filesystem corruption.  And if that happens, since you will then have to boot into Win7 to fix that, and Win7 is then unbootable -- you're in a read bad situation.

Would be better to created a shared data partition, formatted NTFS, that both Win7 and Ubuntu can use.

---

