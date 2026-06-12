---
title: "I've lost Windows need help"
date: 2009-10-10
forum: General Help
---

### Post by JigglyWiggly_ on 2009-10-10
So basically here is how my setup works. I have 3x320s in RAID 0 on an ich9r. So I then added a cheap 160 gig 7200rpm sata hd to it, I installed ubuntu onto it solely. Then I selected in the bios to boot from my RAID, not the 160, and then I get grub error 21... Why the hell did grub install on my RAID. Also ubuntu can't actually see the RAID, by that it sees each individual disc and not the RAID. But that is a big problem, how do I get back my Windows? I got the same error booting into the 160gig hd, then I unplugged the 3x320s in RAID, and installed it. Grub works now for the 160. but I gota get back my Windows... And I don't think I can repair the Windows RAID from Linux, because Ubuntu sees each disc individually!

---

### Post by CharlesA on 2009-10-10
You'd need to boot off the windows cd and repair the MBR (since the bootloader resides there)

---

### Post by JigglyWiggly_ on 2009-10-11
> **CharlesA said:**
> You'd need to boot off the windows cd and repair the MBR (since the bootloader resides there)
I did repair and I clicked the Windows repair button. It gave me a list of options, I selected I have problems booting, Windows said there are no problems... and then restarted... D:

---

### Post by oboedad55 on 2009-10-11
> **JigglyWiggly_ said:**
> I did repair and I clicked the Windows repair button. It gave me a list of options, I selected I have problems booting, Windows said there are no problems... and then restarted... D:

I don't know which windows you're using, but on XP when you boot from the CD and into the recovery console you need to type "fixmbr" after picking your windows installation. That will restore the windows mbr.

---

### Post by JigglyWiggly_ on 2009-10-11
> **oboedad55 said:**
> I don't know which windows you're using, but on XP when you boot from the CD and into the recovery console you need to type "fixmbr" after picking your windows installation. That will restore the windows mbr.
I am on Windows 7 x64.

---

### Post by JigglyWiggly_ on 2009-10-11
Fixed I use bootrec /fixmbr and /fixboot
syntax for anyone who cares is

bootrec /fixmbr

(just doing fixmbr does nothing bootrec has to be infront)

---

