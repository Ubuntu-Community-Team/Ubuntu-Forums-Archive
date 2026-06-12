---
title: "NTFS files missing after rebooted again to hibernated Windows"
date: 2011-10-04
forum: General Help
---

### Post by sunilagham on 2011-10-04
I am using a dual boot system with Windows and Kubuntu(11.04). Most of my files are on windows NTFS partition and I use primarily it from Linux. Its mounted using FUSE.

So this is what happened
1. hibernated windows
2. on next boot, booted to Linux and used it for couple of weeks - without booting to windows
3. booted back to windows (because some an online test worked only on IE and nothing else!, somehow ie4linux wasn't sufficient)

when windows resumed, I noticed that all the files created in those two weeks were missing. Re-booted back to Linux to verity only to find files missing there too. I am guessing windows restored the NTFS filesystem to state when it was hibernated and restored back to that point in time.

I tried tools like ntfsundelete and testdisk. Those missing files are not listed. **[COLOR="Red"]Is there any way to recover those files ?[/COLOR]**

[Also, how did linux mount that drive in RW mode if windows had hibernated and not shutdown ?? I guess linux warns or just mounts drive in read-only mode]

---

### Post by Mark Phelps on 2011-10-04
When Windows hibernates, not SLEEPS, it stores away information such that when it wakens, it can return to EXACTLTY the same state is was in when it hibernated.  That includes the filesystem.

If you write to a filesystem shared with Windows while it is hibernated, chances are that when it awakens, it will rewrite the directory table on the filesystem -- effectively erasing the files you put there.

If this was a shared DATA partition, you should be able to recover the files; if this was your OS partition, recovery is less likely.

If the filesystem was NTFS, the best utility I've seen is a Windows one -- GetDataBack for NTFS.

If you're interested in using GetDataBack, post back here and I'll provide instructions.

---

### Post by sunilagham on 2011-10-04
Thanks for the reply Mark.

I used windows utility "chkdsk" (in fix mode) and rebooted. It recovered all dangling files in found.xxx directory. 

By the way, is there something I have to do so that Linux warns me while mounting shared ntfs drive(or mounts it read-only); in case windows was hibernated ?

---

### Post by prodigy_ on 2011-10-04
> **sunilagham said:**
> By the way, is there something I have to do so that Linux warns me while mounting shared ntfs drive(or mounts it read-only); in case windows was hibernated ?
Actually, ntfs-3g driver used to refuse to mount partitions when it stumbled upon hiberfil.sys. Not sure, maybe they changed it at some point.

---

### Post by sunilagham on 2011-10-06
Thanks !

---

