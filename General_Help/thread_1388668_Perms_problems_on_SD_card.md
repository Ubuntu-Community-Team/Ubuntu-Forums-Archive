---
title: "Perms problems on SD card"
date: 2010-01-23
forum: General Help
---

### Post by Naiki Muliaina on 2010-01-23
I have a memory card that worked fine (and is pretty new). Its a 16 gig micro SDHC. I write to it while its in a Samsung Tocco Lite and have it set to show to the PC as a simple memory card. 

I had no problems writing to it untill last night. Mid way through writing 8 gig to it, it just stopped writing. I found somehow the perms had just changed. I have been trying to write to it scince, im finding i can write to it for about 5-10 secounds after plugging it in then i lose perms. No good to me as i put a lot of films on my phone.

I managed to do a quick format on it and formatted it to FAT (useable on all systems). EXT3 didnt work in the Tocco Lite. It still doesnt work.

I did sudo chown and that didnt work.

I changed the perms in nautilus, that didnt work.

I removed my media folder, that didnt work.

Anyone gots any ideas?

Thankies in advance

---

### Post by mcduck on 2010-01-23
Since FAT and NTFS file systems don't actually support file permissions & ownerships as Linux/Unix uses them (which is why chown and chmod don't work), the permission chnage during file transfer sounds like there was some error with the filesystem that caused it to remount as read-only.

The first thing to try would be wiping the card. Don't do just a quick format but instead remove all partitions from the card and create a new FAT partition. 

If that doesn't work most likely reason is either that the card itself, or your card reader, is broken. In that case try using a separate card reader instead of your phone. If the writes still fail then you'll know the card is broken.

---

