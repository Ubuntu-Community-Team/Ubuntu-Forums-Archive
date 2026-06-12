---
title: "I am reeeeeaaaalllly screwed... Another puzzle"
date: 2009-07-16
forum: General Help
---

### Post by ddivney on 2009-07-16
OK, so after a bad first start with ubuntu that wiped out vista, I'm trying to fix everything.
Here is exactly what happened.

1. Installed ubuntu, it formated my vista partition as linux swap, effectively destroying vista.
2. Tried to restore Vista by using HP's special recovery partiton. Gave error 100e, which means there was an extended partiton.
3. Realized ubuntu was installed on extended partiton.
4. booted ubuntu from live cd and deleted that partiton.
5. Reinstalled on a primary partiton, tried to run HP recovery manager again. Error 1002, and wiped out GRUB
6. Reinstalled ubuntu (for grub), tried to download a vista version that required OEM serial off a torrent.
7. Realized that for some reason, ubuntu will not download ANY torrent from ANY client, and it has nothing to do with my ports.
8. Realized I was in way over my head and wrote this.

What would you do in my position?

---

### Post by dhughes on 2009-07-16
> **ddivney said:**
> OK, so after a bad first start with ubuntu that wiped out vista, I'm trying to fix everything.
Here is exactly what happened.

1. Installed ubuntu, it formated my vista partition as linux swap, effectively destroying vista.
2. Tried to restore Vista by using HP's special recovery partiton. Gave error 100e, which means there was an extended partiton.
3. Realized ubuntu was installed on extended partiton.
4. booted ubuntu from live cd and deleted that partiton.
5. Reinstalled on a primary partiton, tried to run HP recovery manager again. Error 1002, and wiped out GRUB
6. Reinstalled ubuntu (for grub), tried to download a vista version that required OEM serial off a torrent.
7. Realized that for some reason, ubuntu will not download ANY torrent from ANY client, and it has nothing to do with my ports.
8. Realized I was in way over my head and wrote this.

What would you do in my position?

 Start over.

 For a beginner the easiest thing to do if you want to dual boot is to boot from a Linux LiveCD such as Ubuntu. 

 Use a partition application like Gparted to create two (or more) partitions - one NTFS and one ext3 (or ext4).

 Install Windows, get it running correctly, defrag and then reboot with the LiveCD in and set up Ubuntu/Linux choosing to use the ext3 partition.

---

### Post by ddivney on 2009-07-16
I thought so... Problem is vista came preinstalled, and the lack of torrents doesn't let me get another version.
I'm checking HP right now to see if they ship recovery disks to my area (Costa Rica). That might be easier

---

### Post by lisati on 2009-07-16
> **ddivney said:**
> I thought so... Problem is vista came preinstalled, and the lack of torrents doesn't let me get another version.
I'm checking HP right now to see if they ship recovery disks to my area (Costa Rica). That might be easier

Note for future: make recovery discs a.s.a.p. when you first buy a machine, "just in case".

---

### Post by ddivney on 2009-07-16
Don't I know it... I tried, but one of the disks doesn't work. It didn't write properly...

---

