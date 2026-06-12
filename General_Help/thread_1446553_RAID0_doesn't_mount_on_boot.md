---
title: "RAID0 doesn't mount on boot"
date: 2010-04-04
forum: General Help
---

### Post by dmeon on 2010-04-04
First I used fdisk to make new partitions on sda and sdc, which I set to "FD", linux raid autodetect. Then I used the following commands:

```

mdadm --create /dev/md0 -l 0 --raid-devices=2 /dev/sda1 /dev/sdc1
mkfs.ext4 /dev/md0
mkdir /media/raid
mount /dev/md0 /media/raid

```

This worked perfectly.
To save it all, I used this:

```

mdadm --detail --scan --verbose > /etc/mdadm.conf

```

And I added the following line to /etc/fstab:
```
/dev/md0	/media/raid	ext4	defaults	0	0
```

The problem is that when I reboot, and try to use the new raided drive, I get an error saying "/dev/md0" doesn't exist.

Please help!




Edit:

I discovered that I can mount the drive by typing the following into the terminal:
```

mdadm --stop /dev/md*
mdadm --assemble --scan
mount -a

```

But I really don't want to do this every time I restart this machine, especially since it's going to be a small file server at my parents' house.

---

### Post by prodigy_ on 2010-04-04
Is it in your **/etc/mdadm.conf**?

---

### Post by dmeon on 2010-04-04
Yep. I already made sure twice.
This is what it looks like:

```

$ cat /etc/mdadm.conf
ARRAY /dev/md0 level=raid0 num-devices=2 devices=/dev/sda,/dev/sdc

```

---

