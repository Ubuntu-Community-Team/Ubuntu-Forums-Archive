---
title: "Mount folders from SD Card into /home as user"
date: 2009-11-03
forum: General Help
---

### Post by artanis00 on 2009-11-03
I keep data on two filesystems on my laptop: /home on one of the internal SSD HDDs, and an SD card in the reader with things like music, videos, pictures. Basically, large, not-so-important files.

I'd like to take the folders from the SD Card and bind them into the appropriate locations in my home folder, so my music library is on the card, but accessible from ~/Music for example.

I know I can do this with [FONT="Courier New"]sudo mount -o bind[/FONT], but this obviously requires root access, and I'd prefer this be automatic upon login.

I considered trying to do this in /etc/fstab, but there are two issues: 1) I can't check that the needed card is in the reader (if there isn't a card or if a different one is in, and I don't even know if that matters or not,) and 2) the user folder is encrypted, so this needs to happen after the encfs is mounted, preferably via a bash script. I can figure out how to write that if I can get the above command to run as user.

I know this is kind of an odd request for help, but any assistance you can provide is greatly appreciated.

---

### Post by frank_acies on 2009-11-03
something like this in fstab should work:

/dev/sdb1 /home/Music vfat auto,exec,rw,async,user 0 0

or you could just link where ever your sd card automounts to music

ln -sf /media/sdcard /home/Music

---

### Post by frank_acies on 2009-11-03
whoops should be sync instead of async

---

