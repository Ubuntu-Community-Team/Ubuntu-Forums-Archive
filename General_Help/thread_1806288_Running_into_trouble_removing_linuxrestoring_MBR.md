---
title: "Running into trouble removing linux/restoring MBR"
date: 2011-07-17
forum: General Help
---

### Post by sirspazzolot on 2011-07-17
I have another machine now that I'm dedicating to Linux so I'm taking it off of my laptop. I deleted the Linux partitions, GRUB2 died, tried reinstalling Ubuntu to reinstall GRUB, and that didn't help. Followed ```
http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html
``` to restore the MBR, and that said it worked, but now turning on my computer just goes to a black screen with a blinking white line in the top left corner. I deleted the Linux partitions from the Windurrs disk manager, and also used that to extend my NTFS partition a bit. Could that have killed it?

---

### Post by gandaran on 2011-07-17
> **sirspazzolot said:**
> I have another machine now that I'm dedicating to Linux so I'm taking it off of my laptop. I deleted the Linux partitions, GRUB2 died, tried reinstalling Ubuntu to reinstall GRUB, and that didn't help. Followed ```
http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html
``` to restore the MBR, and that said it worked, but now turning on my computer just goes to a black screen with a blinking white line in the top left corner. I deleted the Linux partitions from the Windurrs disk manager, and also used that to extend my NTFS partition a bit. Could that have killed it?
do you still have the 100 MG windows 7 boot loader partition or did you deleted it too? if you have the windows restore disk you should be able to fix the windows boot loader.

---

### Post by sirspazzolot on 2011-07-17
there is a little system partition, yes. I don't have a windows install disk, I'm using the damned HP version meaning Startup Repair is nonexistent. I think I'll try Super GRUB2 Disk while waiting for more answers.

---

### Post by sirspazzolot on 2011-07-17
I can boot into the recovery partition (no startup repair) from Super GRUB2 Disk, but not Windows 7. Win7 does the same thing when I try it from SG2D. I guess that means my Win7 partition lost its bootability somehow. I think I can still mount it. Once this liveCD finishes being made, I'll go make sure it's mount/usable (ubuntu live won't work right now, can't be arsed to troubleshoot when I don't even want to install it.) I guess I can check if the boot flag is gone or I could go in and put all my crap on an external drive and do a clean restore. I dunno. Advise?

---

### Post by sirspazzolot on 2011-07-17
Well, switching the boot flag from the System partition to the win7 partition broke boot more. I guess I'll switch it back to System. The partition is mountable. I guess I'll mount it, get all of my stuff onto my external hdd and then do the factory reset thing and reinstall everything. Not looking forward to it, but I guess it's what I was trying to do by uninstalling Linux in the first place. Why the hell can't OEMs just ******* leave the default Windows recovery tools? I've never had a good experience with restoring Windows before.

---

### Post by Quackers on 2011-07-17
You should have made a Win 7 repair disk while it was booting. With that you can restore the Windows bootloader easily.
You'll have to download one now and it needs to be for the same architecture (32 bit/64bit) as your installed system.

---

### Post by sirspazzolot on 2011-07-17
I could've sworn I made one but apparently I did the wrong option because my disk labeled "Recovery" does the same damn thing as the HP crap labeled "(Factory)Restore". I guess I'll try downloading one and when it inevitably fails (knowing my luck) then I'll proceed with my plan. I've really come to love you since I joined, Quackers. You've helped me whenever something isn't booting right. It's comforting to know somewhere out there is a person so competent, with such a fun name.

---

### Post by Quackers on 2011-07-17
Thank you, however, I think "competent" is pushing it.
You're right about the name though :-)

---

### Post by Bsohm on 2011-07-17
if you can get to a command line prompt within hp's recovery tools you can run  "bootrec /fixmbr " and it should fix your mbr issues bc it redoes your mbr from the saved files within hp's recovery tools

check this its a pretty good kbase article:

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by sirspazzolot on 2011-07-17
I ran bootrec /scanos and it said it found 0 Windows installations. ****.

---

### Post by sirspazzolot on 2011-07-17
I love everybody. was waiting for CD to burn. booted up a cmd and started reading the help stuff on bootsect and bootrec and I actually came up with a solution on my own (ish)! did
```
bootsect /nt60 C: /MBR
``` and rebooted and magic. updated boot code on C: and in the MBR to the right thing or something. Let's hope I remembered how to type code tags there. Thanks, guys. :D

---

