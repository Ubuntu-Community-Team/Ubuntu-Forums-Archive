---
title: "Boot problem kubuntu 9.10"
date: 2009-12-06
forum: General Help
---

### Post by samwilliams507 on 2009-12-06
Can't boot.  I get to a warning that "Ubuntu is running in low-graphics mode."  Hit the OK button and nothing more happens.  If I hit the cancel, I can edit the X .conf file - but that looks OK - has worked for months.  If I select go to console, I never get there. 

this started when I rebooted to backup my info.  Got to that warning.  Rebooted again and got in.  Tar-ed my home directory but didn't write the file to DVD.  Rebooted again but never again got beyond the low-graphics message.  On one reboot, it ran an fsck (without my asking it to) but no change.  I had run updates before the reboot to do backup.

Booted to 9.10 CD.  Ran memory test - all passed.  Booted to Ubuntu.  Ran HD test - it passed (but only seems to be SMART reporting).  I can mount the HD and the directories and several files look good.  I can see the tar file with my backup but can't write it to DVD  (since i'm running from the CD/DVD drive).  Also cannot connect to other computers on my network (Mac Mini OS 10.6, XP box, latest SP) to transfer the file to one of them.  Maybe I don't know correct command.  It's a simple network - no domain - attached to router with DHCP - booting to Ubuntu from 9.10 CD picks up address in same network as other computers.  Tried fsck -p /dev/sda but that errors out and never checks the unmounted hd.

Any help appreciated to fix whatever file is corrupted or to write the backup tar file to DVD or another computer on the network would be appreciated.  If I can retrieve the backup, would be pleased to re-install Kubuntu and restore the tar.  Kubuntu has worked well for several months (since shortly after 9.1 was released).  This is first problem.  

Thanks in advance.  Sam

---

### Post by riste on 2009-12-06
I'm not sure what the problem would be, maybe a conflict with a video driver if you have a custom one, especially if the kernel was just upgraded. Hopefully there is a clue in the logs (if you feel like trying to solve it).  It doesn't really sound like a hard drive problem from what you described, but it's possible.  Most hard drive makers have a test suite they use to tell if a drive is 'failing' and could be replaced under warranty.

Regardless, you should be able to get to the network from a live cd.  Samba/windows network name lookups can be frustrating, I know I've had trouble in kubuntu with them; you might have better success in browsing directly to the IP of the windows or mac computers.  If the network fails you may be able to just connect the windows hard drive to the linux box temporarily; I'm pretty sure the live cd should be able to read and write to the windows drive and copy the backup.

---

### Post by samwilliams507 on 2009-12-06
Thanks for the response Riste.

I finally discovered the root cause.  Spent all day getting my backup off with new USB device, re-installing Ubuntu, updating, loading KDE - got back to the same ."..Running in low-graphics mode" error.  

This time the log files showed the reason.  

There's no longer a driver for the i810 video controller on my Dell Optiplex SX280.  

Aaargh!

---

### Post by giannilmbd on 2009-12-08
Hi,

I had the same problem with two different computers and it seemed I solved it by switching from kdm to gdm.

Gianni

---

### Post by Zorael on 2009-12-08
> **samwilliams507 said:**
> There's no longer a driver for the i810 video controller on my Dell Optiplex SX280.  

Aaargh!
I'm not sure I understand. Were you using the **i810** driver? It has been deprecated (and removed) since a while back. You should use the **intel** driver if you have an i8xx or i9xx chipset.

It should be autodetected and used automatically, unless you've been tinkering with xorg.conf and/or HAL.

---

