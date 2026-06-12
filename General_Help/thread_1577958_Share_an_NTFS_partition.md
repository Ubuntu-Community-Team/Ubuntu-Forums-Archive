---
title: "Share an NTFS partition"
date: 2010-09-19
forum: General Help
---

### Post by feffer on 2010-09-19
I want to create a shared partition with Win7, so I made an NTFS partition. Of course Win7 sees it and has no problem. I can mount it in Ubuntu with this line in fstab:```
# Common data partition for linux and windows -- this is an ntfs partition on /dev/sda9
UUID=my-number-here     /home/user/data     ntfs-3g     defaults,uid=1000,gid=1200,fmask=0113,dmask=0022,nls=utf8     0     0
```This works pretty well, except I don't get execute permissions on my common bin directory. I could get this by mounting the partition w/o restriction, but that seems insecure to me. Is there a way to change permissions on this partition after it is mounted and for one directory only?

Thx,
feffer

---

### Post by srs5694 on 2010-09-19
In theory, you can use mount with the remount option to change mount options, as in:

```

sudo mount -t ntfs-3g -o remount,fmask=0000 /home/user/data

```

When I tried this on a test system, though, it didn't work; I got a message to the effect that remount isn't supported. This may be an NTFS-3g-specific limitation.

Furthermore, even if it did work, it wouldn't help you isolate the effect to that one subdirectory. AFAIK, there's no way to give execute permission to just a specific file or directory on an NTFS partition; it's all or nothing with NTFS (aside from the difference between files and directories).

Why do you need execute permission on anything in NTFS? Ordinarily, you wouldn't want to store Linux executables on NTFS, since they're useless to Windows. Although you might plausibly want to store certain types of scripts or Windows binaries for use by either OS, AFAIK it's always possible to execute them from Linux without execute permission being set.

---

### Post by sandyd on 2010-09-19
> **feffer said:**
> I want to create a shared partition with Win7, so I made an NTFS partition. Of course Win7 sees it and has no problem. I can mount it in Ubuntu with this line in fstab:```
# Common data partition for linux and windows -- this is an ntfs partition on /dev/sda9
UUID=my-number-here     /home/user/data     ntfs-3g     defaults,uid=1000,gid=1200,fmask=0113,dmask=0022,nls=utf8     0     0
```This works pretty well, except I don't get execute permissions on my common bin directory. I could get this by mounting the partition w/o restriction, but that seems insecure to me. Is there a way to change permissions on this partition after it is mounted and for one directory only?

Thx,
feffer
add "users" to the opts.

change UID to your userid

---

