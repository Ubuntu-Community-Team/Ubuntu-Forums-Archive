---
title: "System won't boot"
date: 2010-10-14
forum: General Help
---

### Post by evgsch on 2010-10-14
I have had Ubuntu 10.10 (desktop version, not netbook remix) installed on my Acer netbook for a couple weeks. It has been working fine until a few days ago, when I turned on the computer and began receiving varying error messages -- most commonly it would try to boot to the Realtek Ethernet Controller which would just say there was a media test failure, and other times it would say something like Grub stage 1.5 and then an error number would show up seconds later, like 18 or 25.  I could usually I could let the computer sit for a while, either on or off, and I could turn it off and turn it back on and it would boot up without a problem (after a few tries).  This was very frustrating then...

Now it's worse ... With the exception of earlier this morning, I have been unsuccessful in getting the computer to boot up, and it keeps trying to boot to the Ethernet card.  I could post the message that the computer displays if that would help, but I think it's some case where it just won't recognize the hard drive or ubuntu...

How to fix this?  I really need to get this computer working...it's urgent...so any suggestions please!

---

### Post by evgsch on 2010-10-15
bump thread for response...

---

### Post by VMC on 2010-10-15
Sounds like your BOIS is set to boot from NFS/PXE boot. Have you checked your BIOS settings?

---

### Post by evgsch on 2010-10-15
> **VMC said:**
> Sounds like your BOIS is set to boot from NFS/PXE boot. Have you checked your BIOS settings?

Yes, I have checked the BIOS and the boot order is correct. Also I spent about two hours this evening taking the computer apart -- I took apart the keyboard, motherboard, and hard drive, re-connected it, and then the computer worked, but after I shut it down, and tried to boot up again, I got the same error message as before. Very frustrating.

---

### Post by psusi on 2010-10-15
Sounds like your hard drive might be dieing.  Boot the livecd, and open the disk utility and check the SMART data on the drive.

---

