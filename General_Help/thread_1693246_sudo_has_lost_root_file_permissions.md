---
title: "sudo has lost root file permissions"
date: 2011-02-22
forum: General Help
---

### Post by lancealbertson on 2011-02-22
sudo commands cannot modify files that have root ownership.

I set up a simple RAID1 system with two identical disks under maverick server (no LVM). After the mirror had synced everything up I did a failure test: power down, remove one disk, power up, power down, change to the other disk, power up, power down, put both disks back in, power up. It seemed to work fine after each test in that I could login and be on the network.

Cool.

Except that after I put both disks back in I realized I wasn't on the network. So I did:

   sudo /etc/init.d/networking restart

and, although the network started up fine, I got messages like:

  can't create /var/lib/dhcp3/dhclient.eth0.leases: Read-only file system.

And I realized that "sudo nano arootownedfile" does NOT give me write permissions. This is true for every file I've tried to edit.

When I execute sudo xyz I am asked for my password, and all seems well, except for the file permissions.

Any ideas on what I broke...and how to fix it?

Thx!

EDIT: btw, my user account is a member of adm, dialout, cdrom, plugdev lpadmin, sambashare, and admin groups.

---

