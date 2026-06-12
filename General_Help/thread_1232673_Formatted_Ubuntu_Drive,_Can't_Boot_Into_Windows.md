---
title: "Formatted Ubuntu Drive, Can't Boot Into Windows"
date: 2009-08-05
forum: General Help
---

### Post by mazerrkman on 2009-08-05
I installed Ubuntu yesterday but it wouldn't play nice with my wireless card so I formatted the drive I installed it to. Now I get a Grub error 17 when I try to boot into my Windows 7 installation. Is there a way to get rid of GRUB without being able to log into windows or is there any other way to fix the problem without reinstalling Ubuntu?

I tried using bootsect.exe in a repair command prompt but it didn't do anything.

---

### Post by michy99 on 2009-08-05
You need to fix your Master Boot Sector. If you have a Windows disk, I believe there is a command called fixmbr which will repair it.

---

### Post by mazerrkman on 2009-08-05
Thank you for the quick reply. I tried using fixmbr before to no avail but I believe I was using it improperly. Typing bootrec /FixMbr in the recovery console did the trick!

Perhaps you could answer one more question for me? Now that I am back to using the Windows Vista boot loader instead of grub, I am given the choice between Windows 7 and Kubuntu (which I used for an hour or so before overwriting the install with Ubuntu). I no longer have a Kubuntu install on my computer but it still gives me the option of choosing it. Is there anyway to take it off the list?

---

### Post by michy99 on 2009-08-05
This is just a guess, but try editing the boot.ini file.

---

### Post by JawsThemeSwimming428 on 2009-08-05
Install EasyBCD if you want to use a boot loader from Vista. EasyBCD provides an easy management interface for the Vista boot loader and should allow you to delete the Kubuntu entry.

---

### Post by lvleph on 2009-08-05
> **mazerrkman said:**
> Thank you for the quick reply. I tried using fixmbr before to no avail but I believe I was using it improperly. Typing bootrec /FixMbr in the recovery console did the trick!

Perhaps you could answer one more question for me? Now that I am back to using the Windows Vista boot loader instead of grub, I am given the choice between Windows 7 and Kubuntu (which I used for an hour or so before overwriting the install with Ubuntu). I no longer have a Kubuntu install on my computer but it still gives me the option of choosing it. Is there anyway to take it off the list?

There are a few different ways to fix the MBR.
fix just the master boot record (/fixmbr), the boot sector (/fixboot), or rebuild the entire BCD (/rebuildbcd).

---

### Post by mazerrkman on 2009-08-06
> **JawsThemeSwimming428 said:**
> Install EasyBCD if you want to use a boot loader from Vista. EasyBCD provides an easy management interface for the Vista boot loader and should allow you to delete the Kubuntu entry.

Wow, that was really easy. Sorry for the stupid questions and thanks to everyone for all the help.

---

