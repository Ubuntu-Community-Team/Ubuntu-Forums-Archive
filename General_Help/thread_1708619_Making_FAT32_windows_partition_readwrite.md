---
title: "Making FAT32 windows partition read/write"
date: 2011-03-16
forum: General Help
---

### Post by vaskark on 2011-03-16
I'm having difficulty making my FAT32 drive capable of read/write. I followed the instructions here (http://ubuntuguide.org/wiki/Ubuntu:Maverick#Windows_Compatibility) and added the following line to my /etc/fstab file:

```
/dev/sda4 /media/WinD vfat quiet,defaults,rw 0 0
```

However, when I rebooted the drive is still read-only.
Any ideas?

---

### Post by TechSupportx86 on 2011-03-16
i believe you need to set the umask to 0777(?)

something like (correct me if im wrong):
```
/dev/sda4 /media/WinD vfat quiet,defaults,umask=0777,rw 0 0
```

---

### Post by vaskark on 2011-03-16
I tried what you suggested. Didn't work. In fact, the drive didn't mount at all this time.

---

### Post by TechSupportx86 on 2011-03-17
Well we can try 000 for testing, altho 0777 should have worked, and not mounting because of this seems odd...

copy/paste this into fstab and remount all drives:

```
/dev/sda4    /media/WindD    vfat    defaults,umask=000    0    2

```then just remount all the drives with

```
sudo mount -a
```And a little more info would be helpful. Is the windows drive FAT or NTFS? Also is this windows drive a physical drive or a windows *Partition* on the ubuntu drive? (reason for asking is because of **sda4**)

---

### Post by vaskark on 2011-03-17
It worked! Btw, it's a dual boot system, only 1 physical drive:

sda1: Windows XP (NTFS)
sda2: Ubuntu
sda3: swap
sda4: FAT32 partition

Thanks for all your help ;)

---

