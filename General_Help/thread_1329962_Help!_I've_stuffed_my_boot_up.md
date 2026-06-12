---
title: "Help! I've stuffed my boot up"
date: 2009-11-17
forum: General Help
---

### Post by RobCh on 2009-11-17
**Problem: **
My computer wont boot to windows or ubuntu.  Grub error 22.

**History: **
Have Vista installed.  Tried out ubuntu 9.04 when i first got my HP Pavillion.  Had too much trouble with sound, videos etc etc (ie too much stuffing about) that I rarely ever ran it and always just went to vista.  I have 2x 500Gb HDD's.  On one HDD is Vista.  On the other I divided it in half.  Put ubuntu on 30Gb, 2.5Gb swap, the rest for ubuntu files and the other half for vista files.  

I saw 9.10 was coming out and thought I'd give it another crack.  Ran the boot disk.  It says one HDD is totally free.  The other has half ntfs and 9.04 installed.  Didn't want side by side obviously.  So I went manual set-up.  Deleted the partitions for 9.04.  Had to go go out so didn't have time to continue.  Added the free space onto the ntfs partition for the time being.  Shut down went out.  

Now when I startup it just goes straight to a Grub Error 22.  I have files I didn't back up (stupid I know) on vista on both HDD's.  

If I press my ESC key during the HP splash to choose boot options or BIOS entry all options to conitue booting in whatever way still go to the error.

[B]Plea:
[/B]Can some1 help me sort this out please???  Can I get rid of Grub somehow so only my windows boots up?  Then I'll back up like I should've done and then do a new partition for 9.10.

---

### Post by cta16 on 2009-11-17
What you're looking for is to reinstall MBR(Master Boot Record).

Do you have a Vista disc or the "Upgrade Now" disk?
If you do, boot from it and follow the instructions [here]("http://support.microsoft.com/kb/927392") Once you get to the command line section, type in Bootrec.exe and select the "/FixMbr" option. Restart your computer. If that doesn't fix it, do it again but do the "/FixBoot" option

---

### Post by RobCh on 2009-11-17
No I don't.  Rather than give me a recovery disk with the laptop there was a 11Gb partition which supposedly does the same funtion.  No idea how to use it.

---

### Post by cta16 on 2009-11-17
You don't even have to Upgrade Now disc? I thought it was standard on all HP Pavillions.

---

### Post by cta16 on 2009-11-17
If you really don't have the Upgrade Now disk, then you can download it from [here.]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/")

---

