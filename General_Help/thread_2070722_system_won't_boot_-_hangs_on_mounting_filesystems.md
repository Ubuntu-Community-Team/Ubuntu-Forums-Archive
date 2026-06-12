---
title: "system won't boot - hangs on mounting filesystems"
date: 2012-10-13
forum: General Help
---

### Post by garyozzy on 2012-10-13
10.04 or 12.04 LTS server--I can't remember. Virtualized under kvm on Debian Squeeze. Hangs on boot at this: 

```

[    3.037177] EXT4-fs (dm-0): INFO: recovery required on readonly filesystem
[    3.038109] EXT4-fs (dm-0): write access will be enabled during recovery

```

I *think* I have a bad entry in /etc/fstab. Is there a way I can get to a console before it tries to mount that entry? Ctrl + Alt + F{1,2,3,4} don't work. 

Thanks!

---

### Post by garyozzy on 2012-10-13
I fixed it! 

Booted to a Live CD and mounted the lvm partition, edited the file, rebooted, and away we went!

---

