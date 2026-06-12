---
title: "using &quot;bind&quot; to mount ntfs folders no longer works"
date: 2012-01-10
forum: General Help
---

### Post by blazemore on 2012-01-10
For years, I've mounted my data drive (/dev/sda2) as ntfs under /data.

I have full read-write permissions on /data.

I've used fstab to mount the data folders to the appropriate locations in my home folder:

```
/data/Documents /home/user/Documents none bind 0 0
```

Since the latest lot of distros like Ubuntu 11.10, Mint 12, and even Chakra, which I'm running now, this no longer works, as /home/user/Documents is owned by root and I can't save any files into it!

I've tried using chown and chmod, and it seems to work, but it doesn't actually change the permissions when I check with ls -l.

---

### Post by mcduck on 2012-01-10
It's still an NTFS file system, so of course chown or chmod won't work, the filesystem isn't able to handle the permissions.

What kind of mount options are you using to mount the NTFS partition in the first place? And have you tried adding such options to the bind line in fstab to mount it with the correct permissions and ownership?

---

