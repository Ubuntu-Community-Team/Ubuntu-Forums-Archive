---
title: "Need help in using Root Partition."
date: 2012-04-04
forum: General Help
---

### Post by c2tarun on 2012-04-04
Hi Friends
I have a 30 GB root partition. In the starting I was thinking that linux will use this much of partition :) but now I realized that 26GB of my partition is free and max to max 6 GB's more will be used :(
I use another partition of 130 GB as my home partition.
Now my problem is I want to use that 26 GB space but to use that space I have to use root privileges. Is there any way to make a folder in that space just like my home folder??

---

### Post by nothingspecial on 2012-04-04
Don't do that.

You need to either resize your partitions or make a new one.

---

### Post by oldfred on 2012-04-04
I would not change anything.

I typically make 25GB / (root) partitions and use about 7GB. One site (more on SSDs) suggested that you not use more than about 25% of / to maintain efficiency.  Also temporary space may be needed. For example if you write a backup DVD you may use 4GB of tmp space just for that write.

---

### Post by c2tarun on 2012-04-05
One more thing :( I dont have any swap partition. I have 4 GB ram so I thought I dont need any swap partition. Should I resize some space and allocate it for swap partition??

---

### Post by oldfred on 2012-04-05
Only if you hibernate or run a lot of large programs at once might you need swap. Some suggest some swap just because it may boot a bit faster as it looks for swap and has to not find it before going on. I normally suggest 2GB if not hibernating or the size in GIB of RAM if hibernating.

If running lots of programs or video editing then you should have swap.

---

### Post by c2tarun on 2012-04-05
> **oldfred said:**
> Only if you hibernate or run a lot of large programs at once might you need swap. Some suggest some swap just because it may boot a bit faster as it looks for swap and has to not find it before going on. I normally suggest 2GB if not hibernating or the size in GIB of RAM if hibernating.

If running lots of programs or video editing then you should have swap.


I never did any kind of video of multimedia editing. Right now I am mostly practicing Android development :) I dont think I even require swap partition. I dont have any swap partition and I am not facing any problem. The biggest problem with with swap partition is it take number of counts from total number of partitions and we can have only four partitions. :(

---

### Post by oldfred on 2012-04-05
My new installs (where the drive will never have Windows) are using gpt not MBR so I do not have any limit on primary partitions. But with MBR I used one primary as an extended and have many installs in the extended partition.

---

### Post by c2tarun on 2012-04-05
> **oldfred said:**
> My new installs (where the drive will never have Windows) are using gpt not MBR so I do not have any limit on primary partitions. But with MBR I used one primary as an extended and have many installs in the extended partition.

Here is my partition!! :(


How can I use gpt method that you used, is there any tutorial for it?

Just for a note, I also dont have windows installed on my machine.
sda1 is my main Linux installation which I use for all the purposes. One is home partition, one for movies :) and on is where I test other distros :)

---

### Post by oldfred on 2012-04-05
Best if starting from a new drive. I first tried it on my older 160GB drive which I just totally reformated. Supposedly you can convert, but I never have tried that. I have since used gpt on a 16GB flash drive and a 60GB SSD.

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)
Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
Converting from MBR to gpt:
[http://ubuntuforums.org/showthread.php?t=1454252](http://ubuntuforums.org/showthread.php?t=1454252)

If booting with BIOS you do have to have another small 1MB partition for grub. Unformated & labeled bios_grub.

In a GPT partition map, the 31 kiB area after Master Boot Record where GRUB is usually embedded to, does not exist. When GRUB can't be embedded, its only option is to use blocklists, which are unreliable and discouraged. Thus, you must make a separate "BIOS boot partition" to hold core.img. BIOS Boot Partition only needs to be about 32 KiB in size, although in most cases make it 1 MiB because of partition alignment issues. It can be anywhere on drive.

You can set bios_grub flag in gparted or with command line: In GPT fdisk (gdisk), give it a type code of EF02. Or with terminal:
sudo parted /dev/sda set <partition_number> bios_grub on

Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used without a filesystem for storing GRUB 2 boot code "unknown" filesystem! may be shown in many Partition tools.

---

