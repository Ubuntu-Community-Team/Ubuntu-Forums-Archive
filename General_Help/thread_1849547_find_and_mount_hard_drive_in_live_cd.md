---
title: "find and mount hard drive in live cd"
date: 2011-09-24
forum: General Help
---

### Post by mruschmann on 2011-09-24
I have a old pc running a p3 that cannot boot OS.  So i booted live cd and now i can mount hard drive to back up any files.

i have been to /dev and listed:
found a sda and sda1

cannot mount sda1.  (error msg: cannot fine /dev/sda1 in /etc/fstab or /etc/mtab. Nor can i find a hda to mount either.

Is there some way to find this HD and mount it?  Or is it just gone?

---

### Post by mruschmann on 2011-09-24
i can mount a fd0 but i dont get my command line back

---

### Post by papibe on 2011-09-24
You can check all disks and partitions available using the fdisk command

Could post the result of this command?

```
$ sudo fdisk -l
```

Regards.

---

### Post by mruschmann on 2011-09-24
sudo fdisk -l 

return sda1 as 10 gig but i still get same error msg

---

### Post by papibe on 2011-09-24
Try this:
```
cd
mkdir mnt
sudo mount /dev/sda1 mnt
```
Your files now will be under mnt.

Regards.

Edit: don't forget to unmount it, before shooting down, so you can have a clean shutdown:
```
cd
sudo umount mnt
```

---

### Post by mruschmann on 2011-09-24
sudo mount /dev/sda1 mnt

err msg - you must specify the filesystem type

BTW, Thanks for ur help so far.

---

### Post by Leppie on 2011-09-24
> **mruschmann said:**
> sudo fdisk -l 

return sda1 as 10 gig but i still get same error msg
what is the exact output of that command?
you can select and copy text from a terminal window as well.

---

### Post by mruschmann on 2011-09-24
no but i will type .... things nic is bad.  hold on

---

### Post by mruschmann on 2011-09-24
sudo fdisk -l


Disk /dev/sda: 10.0 GB, 10056130560 bytes
240 heads, 63 sectors/track, 1229 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
disk identifier 0x3f043f03

device boot         start         end         blocks         id         system
/dev/sda1         1         278         2096451         e         w95 FAT16 (LBA)



FAT 16 i am sure ... lol.  Sorry about formatting at end

---

### Post by mruschmann on 2011-09-24
and it doesnt come up with my spaces ... win.

boot - /dev/sda1
start - 1
end - 278
blocks - 2096451
id - e
system - wd95 FAT16 (LBA)

---

### Post by mruschmann on 2011-09-24
many years ago i had a paper with my commands need to do this stuff.  But the wife threw it out.  Thanks so much for help

---

### Post by papibe on 2011-09-24
Does this work?
```
sudo mount -t vfat -o defaults,user,exec,uid=1000,gid=100,umask=000 /dev/sda1 mnt/
```

---

### Post by mruschmann on 2011-09-24
wrong fs type, bad otion, bad superblock on /dev/sda1, missing codepage or helper program, or other error in some casses useful info is found in syslog - try dmesg | tail or so



Before i did that i tried sudo mount -t fat16 /dev/sda1 mnt

error msg - unknown filesystem type 'fat16'

---

### Post by mruschmann on 2011-09-24
with vfat .... same long error message

---

### Post by Leppie on 2011-09-24
try the following:
```
sudo mount -t msdos /dev/sda1 /mnt
```

---

### Post by mruschmann on 2011-09-24
error msg -  wrong fs type, bad otion, bad superblock on /dev/sda1, missing codepage  or helper program, or other error in some casses useful info is found in  syslog - try dmesg | tail or so

[5631.175805] VFS: cant find ext4 filesystem on dev sda1
[5631.175805] FAT: bogus number of reserved sectors
[5631.175805] vfs: cant find valid fat filesystem on dev sda1
[5631.175805] FAT: bogus number of reserved sectors
[5631.175805] vfs: cant find valid fat filesystem on dev sda1
[5631.175805] VFS: cant find ext4 filesystem on dev sda1
[5631.175805] FAT: bogus number of reserved sectors
[5631.175805] vfs: cant find valid fat filesystem on dev sda1
[5631.175805] FAT: bogus number of reserved sectors
[5631.175805] vfs: cant find valid fat filesystem on dev sda1

---

### Post by Leppie on 2011-09-24
it looks like there's some issues with the partition tables.
you should launch a dos/windows system and run a scan to fix the issues.

---

### Post by Hakunka-Matata on 2011-09-24
what Release ubuntu are you running via liveCD right now?

---

### Post by ladlers on 2011-09-24
I had similiar error messages on my actual Ubuntu install, and I tried to reinstall it and that failed. The disk simply crashed. I had to send it back to Western Digital for rma. Luckily (or unluckly), mine was new.

---

### Post by mruschmann on 2011-09-24
I am using 9.4 or 9,10 .... I think the HD is bad.  I gotta sleep on it.  Maybe some method will come to me.

---

