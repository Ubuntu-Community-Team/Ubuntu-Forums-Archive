---
title: "After update: &quot;could not find kernel image:linux&quot; 10.04"
date: 2011-06-22
forum: General Help
---

### Post by ebrioloco on 2011-06-22
Ok, it seems a newbie problem but it isn't. After a while i updated my Ubuntu box remotely through freenx (ssh). My little brother (7 year old) was using the machine in other account. I left and my Windows laptop with the remote session suspend. After that i just logged in again and found that my remote session was closed (It is weird. You usually log in and the account stays open). To shut down the system i just did:

sudo shutdown -P 2

And after a while the system was shut down.

This morning my little brother wanted to play again and he found that the computer doesn't go to grub 2. It just splash with 

syslinux xxxxxxx
could not find kernel image:linux
boot:

i don't have any idea why or how.

I just did: 
1. Reinstall GRUB 2 from LiveCD [http://help.ubuntu.com/community/Grub2]("http://help.ubuntu.com/community/Grub2")
2. Searched this forum and found the same repost problem from newbies with a lost kernel binary image from an usb pen-drive
3. Chroot to the partition and update or reinstall grub2 didn't work either 
4. Change the boot flag and reinstall grub didn't work
5. Cheat with vmlinuz and modify the MBR and create syslinuz.cfg file in order to boot the hard drive as a USB (flag boot is also changed to that partition). Could not find the page is just find it, but I'll post it as fast as i can find it again

All this attempts let me to the same problem again and again

I don't know why i am tossed to syslinux instead of grub

I can't provide you with more information because i don't know how i get trough this. I was just using my machine and it just did'nt work anymore. I can log in and chroot using a livecd but everything seems to be in the right place.

Please help me. I don´t want to reinstall all the toolchains and programs i have until the next LTS.

---

### Post by ebrioloco on 2011-07-01
My little brother did cold reboot during the update (He always did it and i didn't know).

After looking Gparted i noticed that all the hard drives were labeled as boot. A hard drive with only data in ext4 was the one th box was using to boot. So it explains why i was not making any changes while i reintalled grub and so on.

Solution: Delete all boot flags from the other hard drives and reinstall grub.

I went to vacations so i reply to myself a week after... :popcorn:

---

