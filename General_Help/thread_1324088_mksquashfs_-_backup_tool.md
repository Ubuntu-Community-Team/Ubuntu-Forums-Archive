---
title: "mksquashfs - backup tool"
date: 2009-11-12
forum: General Help
---

### Post by tall-male on 2009-11-12
Before Ubuntu 9.10 I used dump en restore for creating backups in combination with LVM-snapshots. Putting it al together in a homebrew script it worked perfectly.

However, since ext4 is standard now, dump en restore do not work anymore. In fact: backups are created but turn out to be corrupted. Searching for a new backuptool to use in (bash) scripts I noticed squashfs.

Creating backups doesn't seems the primary goal for squashfs, but I can use it like:
sudo mksquashfs /home/ /media/USB-stick/backup_home.img

It seems to work well and the backup is compressed as well! Restore can be done for example by:
sudo mount -o loop,ro /media/USB-stick/backup_home.img /mnt/restore

Does anyone have experience using mksquashfs as a backup tool? It all seems too easy; I'm getting suspicious...

I like the option in Gnome to mount *.tar.bz2 files (and more) with the Nautilus option "mount archive". Is that possible with squashfs-files? I'm missing the "mount archive" option using squashfs-files.

---

