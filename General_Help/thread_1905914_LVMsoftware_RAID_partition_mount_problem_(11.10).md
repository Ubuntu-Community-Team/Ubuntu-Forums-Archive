---
title: "LVM/software RAID partition mount problem (11.10)"
date: 2012-01-08
forum: General Help
---

### Post by jewishspawn on 2012-01-08
Hi all,

I've tried my best to fix this and find a solution, but I've run out of ideas and places to go.  I just upgraded from 10.04 to 11.10 and had no problems with the upgrade.  System restarted perfectly afterwards.  Today, I got to my computer which had suffered a kernel panic, restarted and started getting this error on attempting to mount my /home lv:

```
mount: wrong fs type, bad option, bad superblock on /dev/mapper/Armitage-Home,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

the output from the dmesg | tail is:

```
[  998.988541] atkbd serio0: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  998.988545] atkbd serio0: Use 'setkeycodes e059 <keycode>' to make it known.
[ 1007.908187] atkbd serio0: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 1007.908190] atkbd serio0: Use 'setkeycodes e059 <keycode>' to make it known.
[ 1009.332412] atkbd serio0: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 1009.332415] atkbd serio0: Use 'setkeycodes e001 <keycode>' to make it known.
[ 1012.173953] atkbd serio0: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 1012.173957] atkbd serio0: Use 'setkeycodes e059 <keycode>' to make it known.
[ 1017.614657] atkbd serio0: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 1017.614661] atkbd serio0: Use 'setkeycodes e059 <keycode>' to make it known.
```

I have 2 software-RAID 10 as PVs in the LVM and the LVM has 2 LVs one for /swap and one for /home.  I have a separate drive for / that is separate from all of this (at least the system still boots...)

I've tried to run fsck.ext4 and e2fsck on the drive, it consistently ends (after hours) with an error (the exact error message I don't have on hand).

If I try to use a backup superblock for the fsck (either version) I get:

```
fsck.ext4: unable to set superblock flags on /dev/mapper/Armitage-Home

```

I tried a vgcfgrestore on the LVM which worked, but didn't solve the problem.

I'm out of ideas.

Any suggestions?

---

### Post by jewishspawn on 2012-01-08
In case it helps (and to give this a bit of a bump), the error I get from running fsck.ext4 on the logical volume is:

```
Error storing directory block information (inode=123105629, block=0, num=228779): Memory allocation failed
e2fsck: aborted
```

---

