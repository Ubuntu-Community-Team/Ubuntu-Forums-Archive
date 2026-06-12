---
title: "new hardware"
date: 2006-04-30
forum: General Help
---

### Post by Aviatrixie on 2006-04-30
Hi everyone,

   I recently upgraded a lot of my PC's hardware and now my Breezy install is totally "dead in the water". The first thing I upgraded was the cpu (upgraded a 633 mhz coppermine to a 1.4 ghz tualatin using a powerleap pl-neo/t adaptor... a very cool upgrade!) and Breezy would boot and run ok but gave a ton of errors on shutdown. Next I upgraded the cdrom to a dvdrom and the cdrw to a dvdrw. Now my post locks up immediately with and "error 24" message.

   I had read in the forum that there was a boot code that could be used on boot to redetect all hardware but I can't seem to find the post anywhere now.

   Is there a simple fix for this, or would it be simpler to do a clean install at this point?

   BTW, I'm logged on here now using my Breezy live cd. It's working flawlessy! :mrgreen:

---

### Post by r4ik on 2006-04-30
Is this what you are looking for ?

Actually, pretty much of the hardware detectino is done on boot, so you can

Open a terminal and run


sudo init 1

That will stop services and drop you into a prompt in recovery mode. You can also just boot into recovery mode by hitting escape to reveal the grub menu when you boot and then selecting recovery mode

dpkg-reconfigure xserver-xorg #(you are root here, so you do not need sudo)
and then
init 2

to go back into the desktop.

---

### Post by Aviatrixie on 2006-04-30
Hi r4ck :)

   Thanks for the suggestion. Unfortunately, my system was so munged that I couldn't get into Breezy to use a terminal. In fact, I couldn't get far enough into the post to use a cheatcode. While awaiting a reply to this thread I got to thinking and decided to try to mount hd0 with my live CD and it couldn't even see my harddrive. So I tried the same thing with my Beatrix CD which is based on Ubuntu and always mounts all of my drives. It saw the Breezy drive but couldn't mount it, claiming it was an unknown file system. (Beatrix is based on Ubuntu, btw.) I tried my Breezy install CD and it saw the drive ok, so I concluded that my Breezy install was broken beyond my relatively newb linuxite ability to fix. Ergo, I just slicked the drive and did a clean install of Breezy. I'm using it now, in fact! :mrgreen: 

   Now I get to reinstall all of my codecs, additional progs, etc again. Oh well... practice makes perfect. Right?!!! :rolleyes: 

   Thanx!

   Erika

---

### Post by r4ik on 2006-05-01
Pitty you could not drop into recovery mode i was realy curious if that would work or not.
I hope you got all the hardware detected this time and wish you all the best
with the finishing touch.
Long may it run :)
Thanks for your reply.

---

