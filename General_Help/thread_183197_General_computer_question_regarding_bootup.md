---
title: "General computer question regarding bootup"
date: 2006-05-27
forum: General Help
---

### Post by arcanistherogue on 2006-05-27
Hey.  Bootup on my computer is morbidly slow, it takes about 2 minutes for it to get past the POST, and then about 2 more to load up grub fully.   The OSes boot nicely after that, but i think it may have something to do with the drives.

I have been swapping hard drives in and out of my computer and DVD drives, but i reinstalled the Operating systems afterwards.  The main drive that ubuntu is on is my first ATA drive, while windows is on my SATA drive.  It takes forever for it to boot that ATA drive!

Also, sometimes when i reboot it boots up past the POST but it says "Boot device could not be determined, please reset the boot device priority in the BIOS"

I do this, but if i just open and close the BIOS setup it works next time.  

Why does all this happen?  Would it be a Hard drive error with my main ATA drive that ubuntu is installed on?  I plan to install dapper RC soon, so if it is this I might as well go get another drive.

---

### Post by Patrick-Ruff on 2006-05-27
I'm pretty sure the delay is due to a network service...but I never figured out how to disable it. 

just narrowing down the possibilitys.

---

### Post by mumushi on 2006-05-27
i had experienced the same situation before and found out the problem was with my hardware. mine was physical memory issue. try checking your hardware possible things that causes slow booting is your cmos battery or your memory module. Im not sure aabout this but i hope this helps.

---

### Post by arcanistherogue on 2006-05-27
This has been happening ever since I removed my other ATA drive, the 17 GB one.  Ever since then the bootup has been all wonky.

Does that help more?

---

### Post by mumushi on 2006-05-31
you have said you have been swapping drives both ata and sata have been used. i am not sure tho but i guess the slow boot up is due to the boot up sequence. It checks for the drives if the are present or not. you can go to your bios and disable drives take are not present so it only scans for drives present. i hope what i am saying is clear. Just try it and i hope it helps.

---

