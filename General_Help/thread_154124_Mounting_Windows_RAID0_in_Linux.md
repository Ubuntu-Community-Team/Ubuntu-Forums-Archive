---
title: "Mounting Windows RAID0 in Linux"
date: 2006-04-02
forum: General Help
---

### Post by Breepee on 2006-04-02
I'm planning the following setup (with two 200GB drives):

drive 1: 100GB Windows, 100GB RAID0 (one half)
drive 2: 100GB Ubuntu, 100GB RAID0 (the other half)

Those two pieces of 100GB will be used to create a RAID0 (NTFS) volume in Windows, totaling into an array of 200GB. My question is: can this be done?

I by the way wouldn't mind doing it the other way round: creating a Linux RAID0 volume, but mounting that in Windows just is not possible at all I think...

---

### Post by Breepee on 2006-04-03
I know it has something to do with LDM/dynamic disks. Windows would make both disks dynamic and creating the Windows partition and the Windows RAID0 partition isn't the problem. The question is if Ubuntu can be installed onto such a dynamic disk and if the RAID0 array can be mounted.

Does anyone know if this is possible?

---

### Post by Breepee on 2006-04-05
One last little bump...

---

