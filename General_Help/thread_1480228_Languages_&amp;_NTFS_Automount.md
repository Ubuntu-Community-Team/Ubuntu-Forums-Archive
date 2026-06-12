---
title: "Languages &amp; NTFS Automount"
date: 2010-05-11
forum: General Help
---

### Post by [xubz] on 2010-05-11
It's been quite a while since I last used Ubuntu (or Linux in general). I recently did a fresh install of Ubuntu 10.04 x86_64 using MinimalCD, everything else is working fine, except the following:

**1. Languages:** I need support for some indian/asian languages (Hindi/Kannada/Japanese basically). Tried typing "language" in Synaptic, but was overwhelmed. >_<

What packages/fonts do I need to specifically install? It's for just reading the text, Not for using IME/etc.


**2. NTFS Automount:** I remember using ntfs-config to set-up automount of my NTFS partitions, But it does't seem to function now. It gave me this error when I tried to run it using Terminal.

```
[~] $ gksu ntfs-config
Traceback (most recent call last):  File "/usr/bin/ntfs-config", line 102, in <module>
    main(args, opts)
  File "/usr/bin/ntfs-config", line 75, in main
    app = NtfsConfig()
  File "/usr/lib/pymodules/python2.6/NtfsConfig/NtfsConfig.py", line 56, in __init__
    os.mkdir(HAL_CONFIG_DIR)
OSError: [Errno 2] No such file or directory: '/etc/hal/fdi/policy'
[~] $
```


Here is a dump of my **sudo mount -l** after I double clicked the volumes in nautilus.

```
/dev/sdc2 on /media/Music & Video type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions) [Music & Video]
/dev/sda3 on /media/Anime II type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions) [Anime II]
/dev/sda2 on /media/Anime I type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions) [Anime I]
/dev/sdc5 on /media/Anime III & Manga type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions) [Anime III & Manga]
/dev/sdb1 on /media/System type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions) [System]
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdc3 on /media/Dumps type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions) [Dumps]
```

What should be the stuff I should type in /etc/fstab if I need to automount it with write support (and read-only for some select volumes)


Thank you.

---

### Post by mikewhatever on 2010-05-11
Try installing the following fonts:
```
ttf-vlgothic ttf-devanagari-fonts ttf-indic-fonts-core
```

You can run *aptitude search ttf* to see all the fonts and their descriptions.

---

