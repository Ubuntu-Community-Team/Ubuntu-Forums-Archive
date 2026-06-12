---
title: "Mounting NTFS Problem"
date: 2006-04-30
forum: General Help
---

### Post by coolboarderguy on 2006-04-30
Hi All,

I am wishing to troubleshoot an XP box using Ubuntu. How do I mount an NTFS partition? I thought I had it right, but, get the following,


ubuntu@ubuntu:~$ sudo mkdir /mnt/hda
ubuntu@ubuntu:~$ sudo mount -t ntfs /dev/hda /mnt/hda
mount: /dev/hda already mounted or /mnt/hda busy
ubuntu@ubuntu:~$ cd /mnt/hda
ubuntu@ubuntu:/mnt/hda$ ls
ubuntu@ubuntu:/mnt/hda$


I then tried this,


ubuntu@ubuntu:/mnt/hda$ sudo mkdir /mnt/hda1
ubuntu@ubuntu:/mnt/hda$ sudo mount -t ntfs /dev/hda1 /mnt/hda1
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:/mnt/hda$ dmseg | tail
bash: dmseg: command not found
ubuntu@ubuntu:/mnt/hda$ dmesg | tail
[4294888.065000] Bluetooth: HCI device and connection manager initialized
[4294888.065000] Bluetooth: HCI socket layer initialized
[4294890.013000] Bluetooth: L2CAP ver 2.7
[4294890.013000] Bluetooth: L2CAP socket layer initialized
[4294892.171000] Bluetooth: RFCOMM ver 1.5
[4294892.171000] Bluetooth: RFCOMM socket layer initialized
[4294892.171000] Bluetooth: RFCOMM TTY layer initialized
[4297092.972000] NTFS driver 2.1.22 [Flags: R/O MODULE].
[4297269.473000] NTFS-fs error (device hda1): load_system_files(): Failed to load $Bitmap.
[4297269.473000] NTFS-fs error (device hda1): ntfs_fill_super(): Failed to load system files.
ubuntu@ubuntu:/mnt/hda$

I'm using Ubuntu Live CD 5.10 and need to access the NTFS system to delete a specific file that is causing XP to continually reboot. Cheers.

coolboarderguy...

---

### Post by Sutekh on 2006-04-30
Try
```
sudo mount /dev/hda1 /mnt/hda1 -t ntfs -o nls=utf8,umask=0222
```

---

### Post by coolboarderguy on 2006-04-30
Hi All,

it seems I must still be doing something fundamentally wrong,

ubuntu@ubuntu:/mnt/hda$ sudo mount /dev/hda1 /mnt/hda1 -t ntfs -o nls=utf8,umask=0222
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:/mnt/hda$ dmesg | tail [4294892.171000] Bluetooth: RFCOMM ver 1.5
[4294892.171000] Bluetooth: RFCOMM socket layer initialized
[4294892.171000] Bluetooth: RFCOMM TTY layer initialized
[4297092.972000] NTFS driver 2.1.22 [Flags: R/O MODULE].
[4297269.473000] NTFS-fs error (device hda1): load_system_files(): Failed to load $Bitmap.
[4297269.473000] NTFS-fs error (device hda1): ntfs_fill_super(): Failed to load system files.
[4302557.591000] NTFS-fs error (device hda1): load_system_files(): Failed to load $Bitmap.
[4302557.591000] NTFS-fs error (device hda1): ntfs_fill_super(): Failed to load system files.
[4302650.800000] NTFS-fs error (device hda1): load_system_files(): Failed to load $Bitmap.
[4302650.800000] NTFS-fs error (device hda1): ntfs_fill_super(): Failed to load system files.
ubuntu@ubuntu:/mnt/hda$

I have hda and hda1 in dev. The drive is a 38GB drive with the whole drive being 1 Primary partition. Below is the output of df,

ubuntu@ubuntu:/mnt/hda$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/mapper/casper-snapshot
                       2062739   1417821    540112  73% /
tmpfs                   258244         4    258240   1% /dev/shm
tmpfs                   258244     12588    245656   5% /lib/modules/2.6.12-9-386/volatile
tmpfs                   258244        24    258220   1% /tmp
tmpfs                    10240      2884      7356  29% /dev
ubuntu@ubuntu:/mnt/hda$

Anything else needed? Cheers.

coolboarderguy...

---

### Post by PaulL on 2006-04-30
Shouldn't that be /dev/hda1 (or whatever). Is there an entry in /etc/fstab already?

---

### Post by coolboarderguy on 2006-04-30
[QUOTE=PaulL]Shouldn't that be /dev/hda1 (or whatever). Is there an entry in /etc/fstab already?[/QUOTE]

Hi All,

well, that's something I'm not too sure about, eh. I have hda and hda1 in /dev. There is no entry in /etc/fstab. I don't understand why it gives the message that it is either already mounted or busy. Anyone got a clue on this? I've also tried /mnt/hda and l tried umount for both,


ubuntu@ubuntu:/dev$ sudo umount /mnt/hda1
umount: /mnt/hda1: not mounted
ubuntu@ubuntu:/dev$ sudo umount /mnt/hda
umount: /mnt/hda: not mounted



ubuntu@ubuntu:/dev$ sudo mount /dev/hda /mnt/hda -t ntfs -o nls=utf8,umask=0222
mount: /dev/hda already mounted or /mnt/hda busy
ubuntu@ubuntu:/dev$ sudo mount /dev/hda1 /mnt/hda1 -t ntfs -o nls=utf8,umask=0222
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by PaulL on 2006-04-30
I've put an entry in my fstab file for a NTFS partition and it works O.K. (but don't forget the are mounted owned by root and read-only by root). The line is:     /dev/sdb3       /slow_scsi      ntfs    nls=utf8,umask=0222 0       0     (it's a scsi drive of course)

---

### Post by PaulL on 2006-04-30
I've just realised that the partition I gave as an example is world readable.

---

### Post by geek.de.nz on 2006-04-30
```

sudo fdisk -l

```

should show you all your partitions. 

```

mount -t ntfs /dev/hdX /mnt/point

```
(not exactly as written but with the right partition and directory)

should mount the file system.

But anyway, if this partition is NTFS, you cannot delete files from it, because NTFS is mounted read only. However, I think write support has been improved and I could be wrong here. Don't know about the live cd (if it has built in write support for NTFS).

cheers

---

