---
title: "Ubuntu 10.04 Grub Legacy Ate Vista boot option"
date: 2010-05-06
forum: General Help
---

### Post by MasterColdSoul on 2010-05-06
Greetings,

Last night I was switching back and forth between vista and 10.04, I had hibernated 10.04. I don't remember which I logged into but I do know I logged into Ubuntu and Vista and then when I got home and tried to log into Ubuntu and pull up my vista partition to get a file it was gone. 

I just say screw it went to bed and when I woke up I checked and I couldn't log into Vista (Grub Legacy 1.9 something ate it) but I can now access the partition in Ubuntu.

My partition looks like this
/dev/sda1 NTFS SYSTEM VOLUME 1.46gib
/dev/sda2 NTFS Vista 205gib boot
/dev/sda3 Ext4 /home 199gib
/dev/sda4 extended 58gib
*/dev/sda7 ext4 / lynx 19gib
*/dev/sda5 linux-swap 1.9gib
*/dev/sda6 ext4 37gib

* = fake sub partition (forget what it is called)

I need to be able to boot into /dev/sda2 which is my vista drive through grub. I prefer not to switch to grub 2 as I have had issues with it. So sticking with Grub Legacy is best. 

I am on a upgrade from Ubuntu 10.04 RC, fully upgraded

I think this has something to do with hibernation from either Ubuntu, Vista or both.. I may have accidentally put both into hibernation, or booted into one other than the one hibernating.

Anyway to fix this so I can log into Vista?

---

