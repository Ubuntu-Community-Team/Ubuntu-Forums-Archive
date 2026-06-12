---
title: "Serious Boot Issues"
date: 2006-05-23
forum: General Help
---

### Post by Omission on 2006-05-23
Hi, First post and its a cry for help ... sorry!

Basically I have 2 hard drives, i've got windows on my first, and on my second I have a 20gig (NTFS) and a 10Gig EXT3 (Ubunutu). Now everything installed fine and I let grub have the privilage of mangaging this lovely set up. On Reboot this message during boot up:

 "Missing Operating System"

... I awoke from my blackout several hours later. Now I thought i'd try sticking the live CD into the drive and I selected "Boot From First Hard Disk" out of what can litterally be described as Sheer Hope. And Volia, Grub appears, and i can select Ubuntu or Windows and both boot perfectly. The issue i'm having is that I can't access grub without the Live CD booting to the hard disk for me.

Anyone else had this problem? I shall keep combing the forums but thought i'd ask.....

Thanks

---

### Post by Ramses de Norre on 2006-05-23
Are the boot devices in your bios configured correctely?

---

### Post by Omission on 2006-05-23
Well i thought so as i didn't think anything changed but apparently not lol

Changed the boot device from HDD1 to HDD0 and that booted up Grub joy!  :cool: 

Thanks for the quick reply!

---

