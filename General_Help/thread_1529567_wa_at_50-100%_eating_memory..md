---
title: "wa at 50-100% eating memory."
date: 2010-07-12
forum: General Help
---

### Post by truefire87c on 2010-07-12
Recently ubuntu has been having a problem that's really been bothering me. When I boot up ubuntu, it works fine. After several hours (sometimes up to a day) the CPU usage in my docked system monitor shoots up to 50%, and when I do ANYTHING (open a window, change tab in my browser, type), it shoots up to 100% and freezes everything for 5 seconds to several minutes (and occasionaly gets permanently stuck at 100%). This continues happening until I reboot the computer.
 
Looking at the system monitor, it shows that the usage is shared between both cores(they both fluctuate between 0 and 100, with the average being 50-100). My RAM is usually around 1.1GB out of 2GB used, and my swap is between 0 and 50MB of 3.8GB used. Checking the processes, I can see that the only process that's taking up any CPU is the system monitor itself, at 5-10%. when I run top in the terminal, everything is normal except wa. wa is displaying between 50% and 100%.
 
I know wa is the amount of time the computer spends waiting for IO, but does anyone know what's causing it to be so high, or some way to fix it?
 
I'm not using any external storage media, so it couldn't be associated to, say, writing to a flashdrive.
 
I'm running Lucid, and I've tried using Linux 2.6.32-21-generic, Linux 2.6.32-22-generic, and Linux 2.6.32-23-386. The problem persists regardless of which I use. I've not encountered any similar problem running Windows XP Home SP2 on my computer, but I rarely boot to Windows anymore, and even then, only for a few hours at a time.
 
PC Specs:
 
Dell XPS 210
2GB RAM
The drive is partitioned as follows:
20GB for Ubuntu installation. formatted EXT3
20GB for Windows XP Home SP2 installation. formatted NTFS
4GB for Swap partition
400 GB shared space. E: drive on Windows, and /mnt/shared on Ubuntu. formatted FAT32
 
P.S.- I tried killing/ending every process one at a time. Didn't fix it.

---

