---
title: "Help with customized boot USB"
date: 2011-01-10
forum: General Help
---

### Post by CMOS4081 on 2011-01-10
Hello and first thanks to any and all who take the time to even read this post.

I read across several different posts looking for help and to some point I managed to get things working, but I have to ask in the end to get this done for work.

I need to do on a 64bit 10.10:
1-bootable usb, done with pendrivelinux.com util and using caspers persistant fs in order to add remove pacakeges and a in house program.

2-need to completly remove the nouveau module for nvidia graphics.
already tried adding it into the blacklist.conf file and removing via "apt-get --purge remove remove xerver-xorg-video-nouveau" and for some odd reason i still get conflicts with having to unload the nouveau from memory even after rebooting the system.

3-need to start in pure cli with no video at all, I should not have even vesa frame buffer as it interferes with in house soft that must access the hardware.
also tried "update-rc.d -f gdm remove" last time I remember this was done with init 3 set as default. Any help on current equivalent?

4-Is there a way to make the system boot into CLI as mention above as root and run a bash script automatically?
preferably with no need to put the root password.
(I know this last item sounds counter intuitive, the the reason is we have operators who only need to work on the scripted menu)

Last, to all who even bother to read this post thanks, to those who write a reply, double thanks.

---

