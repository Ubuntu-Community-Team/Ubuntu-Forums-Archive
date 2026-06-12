---
title: "My One Windows PC Nuked a 500 GB Hard Drive"
date: 2011-01-01
forum: General Help
---

### Post by gerowen on 2011-01-01
My wife and I have been running Linux on our laptops for a long time now. We had a desktop running Windows XP with a printer and shared 1 TB external hard drive attached to it. The internal hard drive was a 500 GB hard drive. It was previously an external WD MyBook but I accidentally broke the USB board while re-arranging the house one day so it became internal.

Anyway, so it's been running XP for a long time now, no major issues. My account was an administrator, my wife's was limited. My wife received an e-mail and apparently her WoW account had been hacked. I'm not sure how they would have hacked her account; the password was not something obvious that would have been in a Brute Forcer dictionary, and her limited account should have prevented the installation of anything like a keylogger, not to mention my scheduled virus scan had reported nothing. So she received an e-mail saying her account has been hacked and she clicked a link it had to go "re-activate" her account. Apparently Firefox told her it was a malicious site so she closed the browser and came and woke me up (it was early in the morning). I immediately changed all of the passwords on everything, online bills, banks, wireless, etc, and she eventually got her WoW account back. Later that day she started complaining about not being able to delete some of the icons on her desktop (they were in "All users" so a limited account couldn't modify them), so being lazy I gave her administrative rights so she could customise her profile a little more, with the intent of removing them once she had finished. 10 minutes later she got a blue screen. Not a BSOD, just a plain blue screen. Upon reboot I was presented with "No bootable volume found" and not even the BIOS on the machine could detect any information other than the transfer speed of the hard drive. Capacity and everything was unknown.

Prior to this I'd had no problems with the hard drive. No data loss, no noises, scandisks came up clean, so my suspicion is that she had some kind of funk that she'd managed to download onto her profile that was unable to act according to its programming until I gave her admin rights. I've thrown the old 80 GB hard drive back in it and installed Ubuntu 10.10 x64, but I'd like to recover and reuse the 500 GB if possible. Has anybody heard of anything like this and know of anything I can do to troubleshoot the 500 GB hard drive?

---

### Post by TeoBigusGeekus on 2011-01-01
What I'd do:
Connect the hd to a linux pc, copy all crucial data (documents, photos, etc.) and then use gparted to completely format it.

---

### Post by Gunman1982 on 2011-01-01
First to the email: It was a hoax trying to lure you/her to a website where you put in your account data to not reactivate but steal such information. 

Boot a livecd and look at the content of the hdd. I already heard of two people who tried to ... tidy up their harddisk by ordering the directorys neatly. Meaning they moved stuff like the windows folder in a folder named w and thus f*ing up their system. One of them was an Informatics student but she tried it with linux ... -.-

---

### Post by gerowen on 2011-01-01
> **TeoBigusGeekus said:**
> What I'd do:
Connect the hd to a linux pc, copy all crucial data (documents, photos, etc.) and then use gparted to completely format it.

Soon as I track down my SATA to USB adapter I'll give this a shot.

---

