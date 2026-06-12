---
title: "Missing folder on external HD with fat32"
date: 2011-10-22
forum: General Help
---

### Post by xrsimf on 2011-10-22
Hello forum,

I recently sorted my music files on my external HD and now suddenly one folder is missing. I tried fsck, dosfsck and testdisk, though I'm not sure if I used the proper flags. The drive is formatted with vfat32. Whe I try to access the folder via shell, I get: 
```

ls: cannot access MusicFolder: Input/output error

```

dosfsck says:
```

MusicFolder contains a free cluster (...). Assuming EOF.

```

dmesg says:
```

[  400.625214] FAT: Filesystem error (dev sdb)
[  400.625215]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  430.230279] FAT: Filesystem error (dev sdb)
[  430.230281]     fat_get_cluster: invalid cluster chain (i_pos 0)
[13381.919885] FAT: Filesystem error (dev sdb)
[13381.919887]     fat_get_cluster: invalid cluster chain (i_pos 0)
[13381.932275] FAT: Filesystem error (dev sdb)
[13381.932277]     fat_get_cluster: invalid cluster chain (i_pos 0)
[15157.991529] FAT: Filesystem error (dev sdb)
[15157.991532]     fat_get_cluster: invalid cluster chain (i_pos 0)

```

The rest of the filesystem is intact, its just the one folder with lots of files in it...

Can anyone help me please?

Please no advice as to format the whole HD, as this is really not an option...

Kind Regards,
Dave

---

### Post by xrsimf on 2011-10-23
I recovered some data using photorec and ordered a new HD.

---

