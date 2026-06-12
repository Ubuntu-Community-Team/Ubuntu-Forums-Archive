---
title: "Mysteriously disappearing disk space"
date: 2010-04-15
forum: General Help
---

### Post by bmdavll on 2010-04-15
I try to log in with GDM but can't. So I log into the console and I see that I have no space left on my /home partition. This is weird because I dual-boot into Windows, where I access my /home ext3 partition with [Ext2Fsd]("http://www.ext2fsd.com/"). In Windows, I clearly had a couple hundred MB left on that partition. I delete some stuff and I get this:

```

# df
Filesystem    1K-blocks   Used        Available  Use%    Mounted on
...
/dev/sda7     18766564    18241584    0          100%    /home

```

Still 100% used even though I should have >500 MB of unused blocks. What can I do to reclaim the free space? And what caused this in the first place? In Windows, I've only been using Ext2Fsd and [NTFS Link]("http://elsdoerfer.name/=ntfslink") to create junctions to directories in my mounted /home partition. This is the first time I've had this problem.

Thanks for any help.

---

### Post by srs5694 on 2010-04-15
The ext2/3/4 filesystems support a "reserved blocks" setting, in which a certain percentage of disk space (normally 5%) may only be used by root. Your df output indicates 18,766,564 1K blocks on /home, 5% of which is 938,328.2 1K blocks, or about 916MB, so you can't create files as a normal user until over 916MB is free.

You can change the reserved blocks percentage by using tune2fs:

```

sudo tune2fs -m 0 /dev/sda7

```

This command sets it to 0%, which is reasonable on a /home partition. (1% is also reasonable, but there's little point to having it higher than that on /home.)

This feature exists to enable root to log in and do maintenance on a system that's run out of disk space because of user activity. Direct root logins aren't possible on a default Ubuntu installation, though, and this feature is most important on the root (/) filesystem, not on /home or most other filesystems that hold user data.

---

