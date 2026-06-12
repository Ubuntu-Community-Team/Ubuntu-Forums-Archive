---
title: "RAID device &quot;degraded&quot; and blocking boot"
date: 2011-07-10
forum: General Help
---

### Post by Luke.Hoersten on 2011-07-10
When I boot my computer, it drops to busybox shell saying:

```
** WARNING: There appears to be one or more degraded RAID devices **

The system may have suffered a hardware fault, such as a disk drive failure.  The root device may depend on the RAID devices being online. One or more of the following RAID devices are degraded:

Personalities : ...
md0: inactive sdb2[1](S)
     142576768 blocks

unused devices: <none>

You may attempt to start the system anyway, or stop now and attempt manual recovery options. To do this automatically in the future, add "bootdegraded=true" to the kernel boot options.

If you choose to start the degraded RAID, the system may boot normally, but performance may be degraded, and a further hardware fault could result in permanent data loss.

If you abort now, you will be provided with a recovery shell.

Do you wish to start the degraded RAID? [y/N]:
```

When I choose to boot, it seems to work fine but login seems a bit slow. Catting /proc/mdstat yields:

```

md0 : active raid1 sda2[0] stb2[1]
      142576768 blocks [2/2] [UU]

unused devices: <none>
```

I have /dev/sda2 and /dev/sdb2 raid1-ed to /dev/md0

How can I fix this?

---

### Post by Luke.Hoersten on 2011-07-13
bump

---

### Post by Kinnin Vo-Shay on 2011-12-10
Did you recently upgrade from 11.04 to 11.10? If you did, you may have run into this issue:
[URL="http://ubuntuforums.org/showpost.php?p=11388915&postcount=18"]
http://ubuntuforums.org/showpost.php?p=11388915&postcount=18[/URL]

---

