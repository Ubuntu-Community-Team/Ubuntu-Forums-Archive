---
title: "Mounting dm-crypt device at startup"
date: 2011-08-27
forum: General Help
---

### Post by hertzsprung on 2011-08-27
Ubuntu 10.04.3 Server amd64
 
I'm having some trouble getting the following configuration to work:
[LIST]
[*]/dev/sda1 is mounted to /
[*]I have a key stored in /etc which is used by dm-crypt
[*]/dev/sdb1 is encrypted. dm-crypt mounts it at /dev/mapper/crypt
[*]/dev/mapper/crypt is mounted to /crypt
[/LIST]Both mount points are defined in /etc/fstab. When I boot I get the error:
[INDENT]```
 
The disc drive for /crypt is not ready yet or not present
Continue to wait; or Press S to skip mounting or M for manual recovery

```
[/INDENT]
If I understand things correctly, this is because, in upstart, mountall is running before cryptdisk. Really, ubuntu needs to:[LIST=1]
[*]mount /dev/sda1 to /
[*]create /dev/mapper/crypt from /dev/sdb1
[*]mount /dev/mapper/crypt to /crypt
[/LIST]Can anyone explain what *should* be happening at boot time? How should I fix this?

---

