---
title: "Lynx installer not detecting SATA drive"
date: 2010-12-29
forum: General Help
---

### Post by Snips on 2010-12-29
What has changed with the installer between Hardy Heron and Lucid Lynx?

The installer for Heron sees both the SATA drive (Seagate, 160g, master) and the IDE drive (Maxtor, 60g, slave). The installer for Lynx sees only the Maxtor drive.

Currently, my set up is the Seagate drive as /boot and /swap, designated sda 1 & 2 respectively in Heron. The Maxtor drive is /home, designated sdb in Heron.

When running Lynx off LiveCD, the drive designations are switched - Seagate drive becomes sdb 1 & 2, Maxtor becomes sda. Both drives can be browsed and mounted.

GParted sees both drives, though it has the Seagate (designated as sdb in Lynx) flagged as "boot".

Disk Utilities sees both drives, with the Maxtor 'partitioned' as master boot record (though there is no OS installed on the drive) and no partition flag. The Seagate is 'partitioned' as Unknown Scheme and the partition flag is set at bootable.

I've tried changing the BIOS settings but that hasn't done anything. What am I missing or not doing? Though I prefer a fresh install (keeping my /home drive untouched), would it be better in this case to upgrade from the Update Manager?

Any help or suggestions would be appreciated.

---

