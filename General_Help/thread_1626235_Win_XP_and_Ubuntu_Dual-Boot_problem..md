---
title: "Win XP and Ubuntu Dual-Boot problem."
date: 2010-11-20
forum: General Help
---

### Post by Cazzer on 2010-11-20
I have already posted this in the 'Complete Beginner' forum, but I realized it would fit better here.

Hi. I am a complete novice who has tried to install Ubuntu (just Ubuntu, none of the variants) using the Windows installer. When it came up with the 'which OS?' dialog at start-up for the first time, Ubuntu loaded and finished the setup, telling you about the various features of the OS.
After it had finished, a message of some kind flashed along the screen (I didn't see it for very long, all I can say was there was some text and orange dots), and the computer re-booted. I selected Ubuntu at the 'which OS' dialog again, and this is where things started to go wrong.
A dialog then came up asking about the 'GRUB', or something like that. The only option was something to to with Windows XP. I selected this, and was taken back to the 'which OS' dialog. I tried this again several times, before selecting Windows XP and trying to get some help.
Does anyone know what went wrong? (and how I can fix it?)

Other bits of info that may help:

Current OS: 32-bit Win XP Home Edition (SP3)

Computer: Custom, with Intel Pentium (R) processor

---

### Post by garvinrick4 on 2010-11-20
You have choosen to install with WUBI installer? Does Windows still boot and Ubuntu does not boot or does nothing at all boot?

---

### Post by Rubi1200 on 2010-11-20
If this was a Wubi install and you can still boot Windows normally, see here for descriptions of your situation and possible solutions:
[http://ubuntuforums.org/showpost.php?p=9932369&postcount=5](http://ubuntuforums.org/showpost.php?p=9932369&postcount=5)
(this also applies to cases where you did not upgrade, but simply installed via Wubi)

If you cannot boot either operating system, let us know before proceeding with possible solutions.

Hope this helps.

---

### Post by Cazzer on 2010-11-20
> **garvinrick4 said:**
> You have choosen to install with WUBI installer? Does Windows still boot and Ubuntu does not boot or does nothing at all boot?

Yes, exactly. The Wubi installer ran fine, it restarted and finished installing, but I can't boot Ubuntu. Now that I look at the second dialog again, it's asking me *again* which OS I want to boot.

---

### Post by garvinrick4 on 2010-11-20
Follow Rubi1200 seems to have a handle on Wubi install and a fix on the repairing boot.
WUBI install is inside your windows in a folder right next to USERS in C: drive. named UBUNTU.
Good luck partner.

---

### Post by Cazzer on 2010-11-20
Sorry, but I really don't understand what to do. I did do some *looking* (I did not change anything!) around the Ubuntu folder, and I noticed that a folder called 'grub' was empty. Is this a problem?

---

### Post by bcbc on 2010-11-20
Cazzer, did you click on the SKIP button during the install. It sounds like you did. This prevents a necessary package being installed (lupin) which is required by grub to generate the necessary menu entries to boot the wubi install. 

Therefore grub only finds Windows, not Ubuntu and you can only boot Ubuntu.

The best solution is to reinstall and not click on the SKIP button.

---

### Post by garvinrick4 on 2010-11-20
If the fix is uninstall and reinstall. Your uninstall is inside the Ubuntu folder in C: drive.
It is better than using Add and Remove programs in Windows to remove WUBI.

---

### Post by bcbc on 2010-11-20
> **garvinrick4 said:**
> If the fix is uninstall and reinstall. Your uninstall is inside the Ubuntu folder in C: drive.
It is better than using Add and Remove programs in Windows to remove WUBI.
I've had no problem uninstalling from Add/Remove programs - what is different about it?

PS Just run wubi again and it will automatically uninstall first.

---

### Post by Cazzer on 2010-11-21
> **bcbc said:**
> Cazzer, did you click on the SKIP button during the install. It sounds like you did. This prevents a necessary package being installed (lupin) which is required by grub to generate the necessary menu entries to boot the wubi install. 

Therefore grub only finds Windows, not Ubuntu and you can only boot Ubuntu.

The best solution is to reinstall and not click on the SKIP button.

Ummm, yes. That was it. This problem is now solved. Although now something else has cropped up. [http://ubuntuforums.org/showthread.php?t=1627120](http://ubuntuforums.org/showthread.php?t=1627120)

Sorry, I am a complete novice. Anyway, thanks for your help with this issue.

---

