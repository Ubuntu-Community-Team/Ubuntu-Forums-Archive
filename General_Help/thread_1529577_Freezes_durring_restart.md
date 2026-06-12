---
title: "Freezes durring restart"
date: 2010-07-12
forum: General Help
---

### Post by truefire87c on 2010-07-12
When I attempt to restart ubuntu, it freezes as it's turning off (at the screen with the ubuntu logo in the center, and the alternating white/orange dots below). In the end I have to force shut down by holding the power button. Ubuntu shuts down fine if I choose the "shut down" option. I'm only referring to the "Restart" option here.
 
I'm running Lucid, and I've tried using Linux 2.6.32-21-generic, Linux 2.6.32-22-generic, and Linux 2.6.32-23-386. I have the same problem regardless, and my Windows (I have a dual boot set up) restarts fine.
PC Specs:

Dell XPS 210
2GB RAM
The drive is partitioned as follows:
20GB for Ubuntu installation. formatted EXT3
20GB for Windows XP Home SP2 installation. formatted NTFS
4GB for Swap partition
400 GB shared space. E: drive on Windows, and /mnt/shared on Ubuntu. formatted FAT32

---

### Post by audiomick on 2010-07-12
That is odd...

I doubt if I can help you, but it would interest me to know:

What happens if you restart from a terminal. The command is

```
sudo shutdown -r now
```

---

