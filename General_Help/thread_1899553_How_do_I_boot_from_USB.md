---
title: "How do I boot from USB?"
date: 2011-12-23
forum: General Help
---

### Post by Triblaze on 2011-12-23
I put Backtrack on a USB flash drive and I'm trying to boot into it, but I can't seem to figure it out. Disk Utility says that it's marked as bootable and all the files seem correct, so I don't think it's the USB. GRUB doesn't have an option for USB that I can see. I looked in the BIOS under boot order, and it said that "USB Floppy" was disabled, but there were two other USB devices enabled. I forget what they were called.

So how would I boot into it? If USB Floppy is what I need, how do I enable it?

Or can I not boot Operating Systems from a USB drive on this computer?

---

### Post by pretty_whistle on 2011-12-23
null

---

### Post by Triblaze on 2011-12-23
> **pretty_whistle said:**
> null
Meaning?

---

### Post by bobsageek on 2011-12-23
First, don't worry about USB floppy, that should not be it. The other 2 USB boot entries, one of them is likely the USB thumb drive's manufacturers device code. This should be the same data that shows up in Disk Utility. 

Look in Disk Utility, note the disk proper name (some disk have cryptic names), note it, boot into BIOS and see if that name shows up. Likely it does and you just need to chose that device. Also, many recent PCs have a shortcut key to get to a boot menu, often F11 or F12, so you can pick from an assortment of bootable devices, might speed up your trial and error.

[IMG]http://ubuntuone.com/0k25u00uMm5kHJXSLG0Q1R[/IMG]

---

### Post by Triblaze on 2011-12-23
Sorry for not replying earlier, I figured it out after my "meaning what?" post. I just was a bit clueless and didn't put USB boot before harddrive boot. As such, it went to GRUB instead of the USB, and I didn't realize this is what was happening at first. So I just changed the boot order. Stupid mistake.  Anyway, thanks for the help. Sorry I didn't reply sooner, I was too lazy to go downstairs to find the WEP code for the router. Found it anyways though with backtrack. Now to convince my dad to set it to WPA.:P

*I forget, what do I click again to set the thread to solved?

---

### Post by Ms. Daisy on 2011-12-23
I'm glad you found your solution.  Please mark your thread as "solved" by going to "thread tools".

And if you need help in convincing your dad to switch to WPA, have a look at the link in my signature.
Have fun with backtrack! Maltego is a fun tool in there.

---

