---
title: "NTFS Mount chmod folder?"
date: 2006-01-26
forum: General Help
---

### Post by Howcomes on 2006-01-26
How can i properly chmod my /C folder so my user account can access it (C is the mount of my NTFS partition)

Upon further digging i discover this:
```

howcomes@kubuntu:/$ mount /dev/hda2
mount: wrong fs type, bad option, bad superblock on /dev/hda2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

howcomes@kubuntu:/$ dmesg | tail
[4295751.288000] hdd: media error (bad sector): error=0x30 { LastFailedSense=0x03 }
[4295751.288000] ide: failed opcode was: unknown
[4295751.288000] end_request: I/O error, dev hdd, sector 64
[4295751.288000] Buffer I/O error on device hdd, logical block 16
[4295775.111000] NTFS-fs error (device hda2): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.
[4295776.651000] NTFS-fs error (device hda2): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.
[4295776.651000] NTFS-fs error (device hda2): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.
[4297269.310000] ibm_acpi: ec object not found
[4298515.816000] NTFS-fs error (device hda2): parse_options(): Unrecognized mount option quiet.
[4298549.944000] NTFS-fs error (device hda2): parse_options(): Unrecognized mount option quiet.
```

:(

---

### Post by frodon on 2006-01-26
You can't chmod your NTFS partition because NTFS don't support unix rights and ownership, however you can get user read access (because there's no write support for NTFS with linux) following these instructions : [http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)

---

### Post by Jucato on 2006-01-26
there are a few ways to do this (don't you just love variety...)
BTW, after it has been mounted to its own directory, I think it's better and safer to access drives through /media rather than /dev.

1. Change the owner through chown (quite complicated, haven't done this)
2. Change owner through Konqueror, run as root.
3. edit your /etc/fstab so that at boot, that partition will be automatically accessible. This is the best way, I believe.

Just a note from what I've read. It's OK to read from NTFS, but not OK to write to it. If you want to write something to NTFS, the safest way would be to probably have a shared partition with FAT32 file system. Yeah it's an added partition, but at least I'm sure I'm not gonna mess up that other operating system.

EDIT: someone beat me to it. Hmm.. I thought you could chmod NTFS as long as you are root? Oh well... Just verified it, sorry for the misinformation... :(

---

### Post by Howcomes on 2006-01-26
At first i thought it was just a problem with the folder /C , but that i realized it was a problem with the mount. Those instructions worked thx.

Ok so so far, no root account and no ntfs mounts, what else awaits me :P

(both have been resolved now)

---

