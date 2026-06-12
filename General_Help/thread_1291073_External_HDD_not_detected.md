---
title: "External HDD not detected?"
date: 2009-10-14
forum: General Help
---

### Post by armageddon08 on 2009-10-14
My 250GB Transcend External HDD is not getting detected. Help please.

---

### Post by bodyharvester on 2009-10-14
tried these?

lsusb
sudo fdisk -l
df -h

---

### Post by -grubby on 2009-10-14
A few questions:

What interface is it using? USB?
What model is it?

---

### Post by armageddon08 on 2009-10-14
> **bodyharvester said:**
> tried these?

lsusb
sudo fdisk -l
df -h

```
lsusb
Bus 002 Device 002: ID 062a:0003 Creative Labs
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

```
sudo fdisk -l
Password:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003aad1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1306    10485688+   7  HPFS/NTFS
/dev/sda2            1306        8292    56117848+   7  HPFS/NTFS
/dev/sda3            8292        9537    10001880   83  Linux
/dev/sda4            9537        9729     1542240   82  Linux swap / Solaris

```

```
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             9.4G  5.4G  3.6G  61% /
none                  755M  144K  755M   1% /dev
none                  755M     0  755M   0% /dev/shm
/dev/sda2              54G   34G   21G  63% /data

```

---

### Post by armageddon08 on 2009-10-14
> **-grubby said:**
> A few questions:

What interface is it using? USB?
What model is it?

Yup it is USB. It is getting detected on my desktop running PCLOS. However on my laptop running Arch and XP, nothing happens with either OS. It is recieving the power allright, but no detection. I tried with my Jaunty live CD on the laptop, which detects it wonderfully.

---

### Post by armageddon08 on 2009-10-14
Here is my dmesg:
[http://pastebin.com/m28621f9e]("http://pastebin.com/m28621f9e")

---

