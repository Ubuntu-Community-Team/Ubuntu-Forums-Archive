---
title: "Difficulty Mounting mp3 player"
date: 2010-06-23
forum: General Help
---

### Post by Altin on 2010-06-23
Hi
I have a 1G Creative mp3 player that I cant seem to mount. When I attach it a popup appears saying I dont have the privileges to access the drive. I can see under "sudo fdisk -l" that its coming up as a 1G FAT16 drive, at /dev/sdb. When I tried "mount -t vfat /dev/sdb /media/mp3_player" I get the message, 

mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I dont have any trouble attaching any other USB devices & Ive attached this same player to this system before. Im running Eeebuntu 3.0 on an Acer Aspire One netbook.

---

