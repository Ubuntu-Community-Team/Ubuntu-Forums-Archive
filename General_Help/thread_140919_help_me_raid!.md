---
title: "help me raid!"
date: 2006-03-07
forum: General Help
---

### Post by Ocxic on 2006-03-07
I'm having troubles staring my new raid drive, I had it working and now i am unable to mount it. it's a software raid setuo using mdadm. with /dev/hda1 and  /dev/sda4. I was able to restart my computer and remount it once. and scince then I always get a device or resource busy error, but cat /proc/mdstat says that /dev/md0 is inactive. someone help, I would really like this to work.

Fixed
```

sudo mdadm --misc --stop /dev/md0    <---- stops and releases all devices and resources
sudo mdadm -A /dev/md0               <---- Assembles the array for use, mount normally

```

this error could come from not de-activating the array properly during shutdown, or an improper activation at boot, in a look through dmesg i found this if anyone has any ideas i would appretiate it:

```

[4294678.212000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294678.214000] devfs_mk_dev: could not append to parent for md/0
[4294678.217000] md: md0 stopped.
[4294678.219000] md: bind<sda4>
[4294678.220000] md: bind<hda1>
[4294678.225000] md: personality 1 is not loaded!
[4294678.233000] md: mdadm(pid 4764) used obsolete MD ioctl, upgrade your software to use new ictls.
[4294678.234000] devfs_mk_dev: could not append to parent for md/1
[4294678.237000] md: md1 stopped.
[4294678.247000] Attempting manual resume
[4294678.248000] swsusp: Suspend partition has wrong signature?
[4294678.255000] XFS mounting filesystem sda2
[4294678.332000] Ending clean XFS mount for filesystem: sda2
[4294680.023000] md: mdadm(pid 4974) used obsolete MD ioctl, upgrade your software to use new ictls.
[4294680.029000] md: md1 stopped.
[4294680.071000] md: mdadm(pid 4989) used obsolete MD ioctl, upgrade your software to use new ictls.
[4294680.078000] md: md1 stopped.

```

---

