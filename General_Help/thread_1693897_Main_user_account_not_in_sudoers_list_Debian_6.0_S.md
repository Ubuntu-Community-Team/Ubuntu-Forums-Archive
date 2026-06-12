---
title: "Main user account not in sudoers list Debian 6.0 Squezze"
date: 2011-02-23
forum: General Help
---

### Post by CesarOscar on 2011-02-23
When i installed the new version of debian on my laptop to try it out, i noticed that i can't sudo as my main account is not in the sudoers list and i cannot put me in because i'm not sudo.

```
cesar@debian:~$ groups
cesar cdrom floppy audio dip video plugdev netdev powerdev scanner bluetooth

```

I have to enter as a root account but don't know how, plus i forgot my root password. 

note. i dualboot with ubuntu 10.04 and grub is managed by it.

---

### Post by sisco311 on 2011-02-23
You can edit Debian's sudoers file from Ubuntu. Assuming that /dev/sda1 is Debain's root (`/') partition, run:
```
sudo mkdir /mnt/debian
sudo mount /dev/sda1 /mnt/debian
```

Edit the file:
```
sudo visudo -f /mnt/debian/etc/sudoers
```
append it with:
```
cesar ALL=(ALL) ALL
```

Save the changes, close the file and unmount the partition:
```
sudo umount /mnt/debian
sudo rmdir /mnt/debian
```

Reboot in Debian and reset the root password:
```
sudo passwd root
```

---

