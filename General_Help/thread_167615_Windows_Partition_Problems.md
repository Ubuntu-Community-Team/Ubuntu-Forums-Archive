---
title: "Windows Partition Problems"
date: 2006-04-28
forum: General Help
---

### Post by sprinkles on 2006-04-28
I have a windows (FAT32) partition on my drive which I now use to store all my files as my Ubuntu partition doesn't have much space. This worked fine for ages,  until last week when I was downloading using Azureus. There was an error in my torrent, something about it not being able to write to the disk, and not being able to flush (?). I looked in my Windows partition and found that somehow it was read only (it's mounted in fstab as writable by all users). If I reboot it becomes writable, but after my torrent has been going for a while, it goes back to read only.

Anyone got any ideas?

---

### Post by Ensnared on 2006-04-28
I had the same thing happening when using Azureus to download to FAT32 partitions. As far as I figured out, the kernel detects that something goes wrong with accessing the filesystem, and remounts it read-only it to prevent further damage. I suspect this has to do with the way files are handled in bit-torrent because I've seen people experiencing the same with other bit-torrent clients as well.

I don't remember if remounting will work, but you can try it as a temporary workaround other than rebooting.```
mount -t vfat /dev/yourdrive /your/mountpoint -o rw,remount,[...and any other options you've specified in /etc/fstab...]
```

I never figured out how to fix it since I switched to running a command-line client (BitTornado I believe) which monitors a local dir for .torrent-files in screen on a different computer on my network instead. I'm sure there's some way to tell the kernel not to lock the relevant partition if it detects an error, but I can't tell you what it is...

---

