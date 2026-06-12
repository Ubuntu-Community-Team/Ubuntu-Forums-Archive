---
title: "Safely Removing an Ubuntu Partition"
date: 2011-02-11
forum: General Help
---

### Post by Rellik Faros on 2011-02-11
I have a 32-bit laptop running a dual boot with Windows 7 and Ubuntu 10.09 LTS.  I've decided that Ubuntu just isn't for me, and I want to remove the partition and restore the extra hard drive space back to Windows 7.  

Now, a few months ago, I accidentally deleted my Ubuntu partition through Windows Disk Management, and I ended up not being able to boot up my computer.  I can't remember what the exact cause was, but I think it was a problem with the GRUB, and I think I fixed it by reinstalling Ubuntu. Does anyone know how I can safely remove the Ubuntu partition without having to go through all this again?

---

### Post by Irony on 2011-02-11
You have to use your windows CD and fixmbr (google for your version of windows) once that is done boot up to check that it boots then just format your ubuntu partition.

---

