---
title: "external drive won't mount"
date: 2009-09-09
forum: General Help
---

### Post by bobke on 2009-09-09
Have a maxtor 250gb HD that is connected via a manual switch between winxp computer and linux computer. It has been faithfully mounting for about three years both. It will mount on win but not on linux. Tried two different partitions, both with Ubuntu but still won't mount.  I get this:

ERROR: directory /media/maxtor is not empty.  Error: could not execute pmount

I found a post that said try 'sudo blkid' but that only shows the UUID. Maybe that's where the prolem is? But I don't know how to fix it. I tried unplugging the HD and swithching the switch, but still get the error msg. Oh! on this Ubuntu partition says 'fsck failed' upon boot, if this is of any consequence.

---

### Post by dstew on 2009-09-09
What is in the directory /media/maxtor?

---

### Post by bobke on 2009-09-09
> **dstew said:**
> What is in the directory /media/maxtor?It's empty. But the icon shows in the task panel and says unmounted. When I click mount, that's when I get the error msg.

---

### Post by dstew on 2009-09-09
How is the disk connected to the computer?

---

### Post by bobke on 2009-09-10
> **dstew said:**
> How is the disk connected to the computer?Connected via usb. But it is working on the computer because it mounts on mepis/hda2. I noticed this happening right after I installed Hardy(upgrade from Dapper) on hda5. So now I have two Ubuntu's - Edgy/hda1 and Hardy/hda5. I'm wondering if they are conflicting. They didn't when Edgy was on both hda1 and hda5. Also when I upgraded to Hardy I noticed that some of the installs failed (don't know which ones), but if these install failures affected the mounting of the ext drive then why should it affect Edgy/hda1? My flash USB drive works on Edgy/hda1 but not on Hardy/hda5. 

The ERROR say's: 

'Wrong fs type, bad option, bad superblock on /dev/sde1, missing codepage or helper program, or other error. In some cases info is found in the sys log try: dmesg|tail or so."

---

### Post by dstew on 2009-09-10
So, the drive used to work fine on Edgy/hda1 and Edgy/hda5, but when you upgraded Edgy/hda5 ot Hardy/hda5, the drive doesn't work on either Edgy/hda1 or Hardy/hda5, correct? But, the Edgy/hda1 USB system seems to work, because you can mount a USB flash drive. And, it can't be the drive itself, because it works correctly on mepis/hda2.

You noticed some install errors on Hardy. My guess is that the Hardy system is not in good health. Sometimes upgrading will not go perfecty, and the system does not work well. You might try installing Hardy on /dev/hda5 from a CD.

But, I still can't figure out why your Edgy system would be affected. One possibility is that the external drive or the USB hardware had some firmware changed, or some BIOS settings were changed that affect how the USB system works. You might check your BIOS settings, and see if there are any USB settings that can be fiddled with. I don't have any other ideas at present.

---

### Post by bobke on 2009-09-10
> **dstew said:**
> 

But, I still can't figure out why your Edgy system would be affected.  OK, you understand it all right! I noticed that the fsck failed on Edgy/hda1, so this might be a UUID problem because of the upgrade to Hardy was first a delete of Edgy/hda5- then installed Dapper/hda5- then the Hardy upgrade. Confusing?  Well, I deleted hda5 and installed Edgy, there, in the place of Hardy. Both the ext Maxtor HD and USB Flash drive, now mount. So hda5 is now OK... But on Edgy/hda1 the Flash USB mounts but the ext Maxtor HD doesn't. I googled some questions about the fsck and found someone who had problems mounting drives as a result of the UUID's being out of place.  Does this sound like maybe the culprit? Or something else too?

---

