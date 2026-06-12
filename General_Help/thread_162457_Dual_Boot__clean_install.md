---
title: "Dual Boot / clean install"
date: 2006-04-19
forum: General Help
---

### Post by Matten on 2006-04-19
For now I have only Ubuntu 5.10 on my PC. Now I would like to erase everything and start again to have Xp and ubuntu in dual boot. (First Xp and then Ubuntu I asume....)

Is there anyone that can help me? Or is there someone who knows a bootable disk that can sweep everything from my disk?

---

### Post by markr on 2006-04-19
Easiest way to do this is to stick in your WinXP disk and install it first (instruct it to reformat the entire hard disk).

When WinXP is installed, you can then stick in the Ubuntu disk and install as normal (instructing it to resize the winXP partition to suite your needs), Ubuntu will resize, install GRUB etc and you are home free.

One thing to consider is the creation of a seperate partition that both Windows and Linux can read/write so you can share data between the operating system (FAT32 would do the trick, or an EXT2/EXT3 read/write driver for Windows which I use)

Let me know if you need more details.

Mark.

---

### Post by Malta Soron on 2006-04-22
I got a question. According to the [MS knowledge base](http://support.microsoft.com/kb/310525/en-us) FAT32 supports disks up to two terabytes. Would it be a good idea to format the XP partition as FAT32, so you could acces it from Ubuntu if you wanted to?

---

### Post by Ramses de Norre on 2006-04-22
You'll have a few disadvantages, fat32 does not have journalling, which enlarges the risk of data coruption on reseting the machine. You'll also get a lot more fragmentation. But when you're not going to use win much it might be a good plan. When you'll use it quiet a lot I'd use ntfs though.

---

