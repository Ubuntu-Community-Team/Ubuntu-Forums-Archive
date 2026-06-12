---
title: "Flash Drive Changes Name on backup"
date: 2010-03-15
forum: General Help
---

### Post by thecaptainzap on 2010-03-15
Hello all,

I'm having an interesting problem, and I'm not sure what the root of it is.

I'm running Xubuntu 9.10 on an older machine. I've got a flash drive (called "TF_FLASH") plugged into a USB hub. I am using simplebackup to backup my documents (I'm writing my thesis and that is really the only important thing on this computer). 

The problem I am having is this: simplebackup will run and backup my files once or twice (I have it set up to go overnight). After that, though, the name of the flash drive changes (from "TF_FLASH" to "TF_FLASH_" - note the extra underscore at the end). So, simplebackup cannot find the drive. If I go into the settings of simplebackup and change the backup destination to "TF_FLASH_" it will work once or twice, but the drive will change to "TF_FLASH__" - again an additional underscore.

I don't know if the name change is being caused by Xubuntu, simplebackup, or some other method. The USB hub is a cheap one, but I don't think that's the problem (my mouse is plugged in and continues to function, etc.). Any thoughts on what might be causing this?

Thanks in advance for your help!
-Tim F.

---

### Post by thecaptainzap on 2010-03-15
Hmm so I've been poking around using GParted. It looks like the label is staying the same ("TF_FLASH") but the mount point is changing (to "TF_FLASH_").

In my /media/ folder, there is both a "TF_FLASH" and a "TF_FLASH_".

Any thoughts?

---

