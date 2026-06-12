---
title: "cp command - error message?"
date: 2009-12-11
forum: General Help
---

### Post by ajk32 on 2009-12-11
Hi everyone,

I am trying to copy all my files from a raid5 array onto an external USB hard drive (I have an unanswered post over on the server section wrt my server OS hard drive failing!)

I have resorted to copying all the data off so I can mess around without fear of losing anything.

I am at the busybox prompt of my (very messed up) file server. I issue to commands:

```
mount /dev/md0 /server
```

which mounts fine, I can see all my files. Then I mount the external HD:

```
mount -t ntfs /dev/sdf1 /ext_HDD
```

I had to include ntfs otherwise the HDD would not mount. I then try and copy *everything* off by issuing:

```
cp -pr /server/* /ext_HDD
```

Which seems to be fine, however, I am getting rather a lot of errors:

```
unable to stat '/server/......' invalid or incomplete multibyte or wide character
```

So I know it must be something to do with non-supported characters in the file system, how can I mount the external HD in such a way that this error does not appear?

Many thanks in advance!!
Andrew

---

### Post by falconindy on 2009-12-11
2 possibilities:

1) Use ntfs-3g instead of ntfs.
2) Add "-o iocharset=utf8" to the mount invocation.

The native NTFS driver for linux is extremely primitive.

---

### Post by ajk32 on 2009-12-11
Cool, I'll try those. Is there any any way of verifying that all the files have copied over? I've got errors, but they are dissapearing off the screen, so I don't know how many files it's skipping. Even just a check on the size on disk for all the files, kinda like "dir *.*" in the dos days (shudder).

Thanks! Andrew

---

### Post by falconindy on 2009-12-11
You can use `du -sh <target>` to compare the size of each directory.

---

