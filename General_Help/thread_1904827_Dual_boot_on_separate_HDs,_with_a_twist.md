---
title: "Dual boot on separate HDs, with a twist"
date: 2012-01-05
forum: General Help
---

### Post by nick roto on 2012-01-05
My main system has twin 500GB SATA disks in a RAID1 array running Win7 plus a single disk of the same type currently used just for backups and not part of the RAID. I want to start experimenting with Ubuntu without changing (for now) how it appears to other users, except that I will move backups to an external drive. I can then use the third HD for Ubuntu.
I have seen some tutorials on how to do this - any recommendations for the clearest and best are welcome. However, they generally recommend the boot sequence starts with the Ubuntu drive so that the required OS can be chosen from there.
I would prefer the system to boot to Windows by default and only enter Ubuntu by specific action, either by exiting from Widows or by interrupting its boot. Can anyone tell me whether this is possible, and how to achieve it?

---

### Post by topsites on 2012-01-05
How well do you tolerate pain?

It sure does seem they generally recommend the boot sequence starts with the Ubuntu drive so that the required OS can be chosen from there... Thus it appears at present the only (and best) way to achieve a multi-boot system is by selecting your OS upon boot, at least that's what I've always done, it presents me with the options on booting and I simply press the one I want, then let it keep booting.

Just, you know...
It has been my experience, especially with Linux, go with the flow.

---

### Post by RagingLoon on 2012-01-05
I had to create an account just to answer your question because, the easiest way with multiple HDD's is quite simple. Just install Ubuntu to your spare 500GB HDD like it's your only HDD and press F10 or whatever it is on your bios and either select the HDD with Windows or select the HDD with Ubuntu. 

Set the drive with Windows to boot as default in your bios and you'll only have to F10 to get the boot menu for Ubuntu. It's that simple. :)

FYI: If you have the room throw some more HDD's in your system with any  other OS you desire. And to be extremely safe and foolproof, just unplug  your Windows HDD's/RAID 1 while you install Ubuntu.


Hope this helps.

---

### Post by alphaamanitin on 2012-01-05
RagingLoon is right, this is the way I set my machines up.  Though it is not always F10 depends on your computer (or motherboards) manufacturer.  Make sure when you install Ubuntu you put the bootloader on the same drive as ubuntu, not the window's drive.  In fact the easiest way may be to unplug your HDs with windows on it during the ubuntu install.  

AlphaA

---

### Post by efflandt on 2012-01-05
I have done that numerous times.  If you know what you are doing you don't necessarily need to disconnect your other drive(s), just select **Other** during install partitioning and make sure that you select the proper drive to put partition(s) on and the drop down list at the bottom about which drive to install grub.

My main (Dell) desktop has 3 partitions for Win7 with DOS/Win mbr. 64-bit Maverick (10.10) is on sda4 with grub on sda4 (no swap since 8 GB RAM).  So if Win7 boot partition is marked as boot partition, it boots just Win7.  If I mark sda4 as boot partition (from live install iso on bootable USB) then it would bring up grub from sda4 to select what to boot.

But more to what you want to do, I have 64-bit 11.10 with its grub on sdb, that I currently use to boot everything, with BIOS set to boot that drive.  But if I wanted have Win7 transparently boot normally, I would just use that as boot drive, and press F12 during BIOS splash screen to select an alternate boot device.  Some computers may use a different key in BIOS splash screen to select alternate boot device (sometimes Esc).

Similarly on a new tablet PC with detachable keyboard (Acer Iconia W500P), it normally boots Win7 Pro, but I enabled BIOS F12, so I can boot regular complete install (including grub) of 64-bit 11.10 from internal USB connected SDHC (sdb) by selecting alternate boot device.

If you go the disconnect other drives route, just be aware that from grub menu **e** (edit) you "might" need to point to the proper **root=** after reconnecting the other drives, and after successfully booting doing **sudo update-grub**.  Using UUID's that should be automatic even if drive devices change, but sometimes it is, and sometimes not.

---

### Post by alphaamanitin on 2012-01-05
The UUID thing is really annoying.  I had lots of issues for a while with them breaking (I booted ubuntu from a external HD on a laptop via the BIOS method).  I would have to go in and change it every now and then, but lately no problems so maybe it is fixed.  BTW-UUID id default now so you shouldn't need to update your grub, not saying that it won't happen though, but you shouldn't need to do so.

AlphaA

---

### Post by nick roto on 2012-01-05
Everyone agrees that seems the most straightforward way. Thanks for taking the trouble to answer, I better mark it as solved.

---

