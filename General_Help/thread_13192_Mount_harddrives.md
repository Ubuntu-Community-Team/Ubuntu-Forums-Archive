---
title: "Mount harddrives?"
date: 2005-01-29
forum: General Help
---

### Post by Enki on 2005-01-29
As I'm writing this, I am running Hoary Live from CD, and I love it so far.

One question: is it possible to access my harddrive (NTFS)? I've tried mounting it, but can't get it to work. As I'm a complete Linux noob, could someone spell it out for me?

Thanks

update:
Got it working using this line in fstab:
```
/dev/hda1 /mnt/hda1 ntfs noatime,defaults,users,ro,umask=0 0 0
```

---

### Post by oracledarren on 2005-01-29
hmmm not sure on the NTFS side of things but a general rule of thumb is to create a folder the same name as the device partion in /mnt eg. /mnt/hdb1

then use either ro for readonly or rw for read write in the following line

mount -ro /dev/hdb1 /mnt/hdb1

if all is well when you look in the /mnt/hdb1 folder that will be the other drive

hope this helps

Darren

---

### Post by Enki on 2005-01-29
Thanks, but that results in this error mess.:
"mount: can't find /mnt/hda1 in /etc/fstab or /etc/mtab"

edit:
googled up [this site](http://www.tuxfiles.org/linuxhelp/fstab.html), added this line to fstab:
```
/dev/hda1 /mnt/hda1 auto defaults 0 0
```

...which led to this when trying to mount:

```
root@ubuntu:/etc # mount -ro /dev/hda1 /mnt/hda1
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@ubuntu:/etc # dmesg | tail
ACPI: Power Button (FF) [PWRF]
lp0: ECP mode
lp0: ECP mode
ibm_acpi: ec object not found
lp0: ECP mode
apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
apm: overridden by ACPI.
NTFS driver 2.1.22 [Flags: R/O MODULE].
NTFS-fs error (device hda1): parse_options(): Unrecognized mount option /dev/hda 1.
NTFS-fs error (device hda1): parse_options(): Unrecognized mount option /dev/hda 1.
```

so... any ideas?

---

### Post by blitze on 2005-02-05
For what it's worth, this got my NTFS partition happening on the live cd.
The partition is recognised as hda2 so my line in fstab is

/dev/hda2 /mnt/hda2 auto defaults,users,umask=0 0 0

This allowed me to acces the partition as a normal user on the live CD.  8) 
just open a root terminal, cd to etc directory and use nano to edit your fstab, create the corresponding mount point then mount it using a normal terminal or file browser.

---

