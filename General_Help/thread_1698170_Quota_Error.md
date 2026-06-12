---
title: "Quota Error"
date: 2011-03-01
forum: General Help
---

### Post by fairplay89 on 2011-03-01
I am setting up an LTSP server. This forum is of little help on that front. I am however trying to add/enable/whatever quotas.

5 trillion sites say edit /etc/fstab and add grpquota to the file. 

See: [http://www.tcpdump.com/kb/os/linux/linux-quota-tutorial/configuration.html]("http://www.tcpdump.com/kb/os/linux/linux-quota-tutorial/configuration.html")

My fstab file looks NOTHING like the one they show. 

This is mine:
```

# /etc/fstab: static file system information.

#

# Use 'blkid -o value -s UUID' to print the universally unique identifier

# for a device; this may be used with UUID= as a more robust way to name

# devices that works even if disks are added and removed. See fstab(5).

#

# <file system> <mount point> <type> <options> <dump> <pass>

proc /proc proc nodev,noexec,nosuid 0 0

# / was on /dev/sda1 during installation

UUID=36cb2676-a3fc-469e-899e-2ac2805dd22c / ext4 errors=remount-ro 0 1

/dev/sda5 none swap sw 0 0

```

I just need to know how to add quotas for a group known as students. I have read 4 pages of Google tutorials, none of which show the same fstab format that I have.

---

### Post by fairplay89 on 2011-03-02
Bump, I really need help on this. Why does it seem that every question I ask on these forums gets ignored?

---

