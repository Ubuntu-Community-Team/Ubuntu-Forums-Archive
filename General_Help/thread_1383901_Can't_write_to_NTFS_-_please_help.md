---
title: "Can't write to NTFS - please help"
date: 2010-01-17
forum: General Help
---

### Post by Chaos_Spear on 2010-01-17
So I'm dualbooting XP and Kubuntu on my laptop, and want to move some files from my ext3 part to the NTFS part.  Mounting it goes fine, but can't write, create folders, etc. to the NTFS part.  Started looking for people with similar problems online and found the guide on this site, so I installed ntfs-config and went through the steps, checking "Enable write to internal device", etc..  Still no good.  I tried manually putting in the write option on the mount command, no flags comes up but konsole still says "Operation not supported."  Any help?

EDIT: sorry, dual-booting Vista and Kubuntu Jaunty

---

### Post by Leppie on 2010-01-17
> **Chaos_Spear said:**
> so I installed ntfs-config and went through the steps, checking "Enable write to internal device", etc..  Still no good.  I tried manually putting in the write option on the mount command
which mount command? using ntfs-config you shouldn't need a command to mount the partition.
have you checked if you're in the fuse group?
```
groups
```if fuse is not listed, you can add yourself like this:
```
sudo adduser <username> fuse
```
or do you still have a fstab entry for this partition?

---

### Post by Chaos_Spear on 2010-01-18
Well, actually I tried writing to a different folder in the filesystem and it worked fine, so I'm guessing Vista only allows write access to certain parts of the filesystem, in any case it doesn't seem to be a Linux problem.  Thanks anyway!

---

### Post by Leppie on 2010-01-18
> **Chaos_Spear said:**
> Well, actually I tried writing to a different folder in the filesystem and it worked fine, so I'm guessing Vista only allows write access to certain parts of the filesystem, in any case it doesn't seem to be a Linux problem.  Thanks anyway!
i have a machine with ubuntu and vista as well and i've never experienced issues not being able to write to the vista partition. as long as you're not trying to write to folders using junction links i suppose it should be fine.

---

