---
title: "Uninstalling Ubuntu"
date: 2011-07-05
forum: General Help
---

### Post by User1138 on 2011-07-05
Since I'm clearly not ready for Linux, I'm giving up and uninstalling it. A thread on this forum recommended using bootitng, but I have Windows 7 64bit rather than 32bit. I live in the UK and don't have a credit card, so paying for the latest version is not possible. Any ideas on what I should do? Oh, and I can't find my Windows Live disc. Not sure I even have it anymore. Am I stuffed?

---

### Post by dFlyer on 2011-07-05
I'm assuming you were dual booting windows and linux. If thats the case Windows 7 should still be there. To delete your ubuntu partition just boot into the live cd and use disk utilities to delete your linux partition. You will have to use the windows 7 disk to fix the mbr so you don't get grub.

If you were using Wubi all you have to do is just uninstall ubuntu from windows.

If you were just running Ubuntu and not dual booting just install windows 7 from the windows cd.

---

### Post by seawolf167 on 2011-07-05
First overwrite the MBR with the Windows 7 MBR using a recovery disk ([example]("http://www.addictivetips.com/windows-tips/windows-7-recovery-disk-boot-disk/")).

Then you should be able to boot to your Windows 7 install then open it's partition editor (Right click "My computer" select manage, then select "disk management"), then delete the Ubuntu partition and expand your Windows partition into it's space.

---

### Post by toor58 on 2011-07-05
Before you do anything please follow the instructions in this link:

[http://ubuntuforums.org/showthread.php?t=508927]("http://ubuntuforums.org/showthread.php?t=508927")

This will restore your machine without any probs.

Please return when you feel ready. Thank you and good computing.

---

### Post by Mark Phelps on 2011-07-05
Everyone seems to be assuming that (1) you have a Win7 repair disk of some kind and/or (2) you can boot into Win7 and do the repairs from there.

From your comments, I'm guessing that neither is true.

There is a way to restore the MBR using LILO, but unfortunately, I can't find the link with the details at the moment.  Hopefully, one of the others will come along and provide that info.

Without that, since the typical link that folks provide to the famed Win7 Repair CD images has been taken down, you're basically stuck.

---

