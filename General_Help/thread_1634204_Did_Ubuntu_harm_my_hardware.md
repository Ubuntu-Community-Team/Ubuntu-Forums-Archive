---
title: "Did Ubuntu harm my hardware?"
date: 2010-11-30
forum: General Help
---

### Post by kris7 on 2010-11-30
Hello I have quite a rough time... I bought a new laptop Toshiba satellite with pre-installed windows 7. Of course as I was using ubuntu in the past 6 months I decided to wipe the hard drive and to install ubuntu on top of it.
It did not work as I expected. I was't able to start the ubuntu 10.10 installation. Later I succeeded only with the net book version. So I thought I shall install windows 7 and use ubuntu from a VM. Sadly I found that the computer didn't want to boot the windows 7 cd... Do you think that the ubuntu harmed the bios maybe?
What about grub 2 could it harmed the bios? I am able to boot any linux cd but no windows' boots up.

Regards,
Kris

---

### Post by Grenage on 2010-11-30
> **kris7 said:**
> Hello I have quite a rough time... I bought a new laptop Toshiba satellite with pre-installed windows 7. Of course as I was using ubuntu in the past 6 months I decided to wipe the hard drive and to install ubuntu on top of it.
It did not work as I expected. I was't able to start the ubuntu 10.10 installation. Later I succeeded only with the net book version. So I thought I shall install windows 7 and use ubuntu from a VM. Sadly I found that the computer didn't want to boot the windows 7 cd... Do you think that the ubuntu harmed the bios maybe?
What about grub 2 could it harmed the bios? I am able to boot any linux cd but no windows' boots up.

Regards,
Kris


No.  Ubuntu could not have damaged your hardware.

---

### Post by kris7 on 2010-11-30
Any ideas why other than linux cds wont boot?

---

### Post by Grenage on 2010-11-30
My guess would be that the CDs that won't boot are either damaged, or you're not pressing a key when prompted to do so.

Have you tried another Windows disc?

---

### Post by kris7 on 2010-11-30
So far windows 7 and vista... I guess they might be corrupted for some reason.

---

### Post by Grenage on 2010-11-30
It's possible that they are damaged, bit you'd be unlucky for them to both have issues.  Try copying the CD; you may have more luck booting from the copy, if it copies at all.

---

### Post by TBABill on 2010-11-30
Will they start up in another computer? Since you could not install Ubuntu and these disks won't read it sounds like you could just have a CD drive issue. I'm not certain, of course, but could you see if they will start up in another computer? The windows disks won't actually install anything AFAIK without hitting the prompts to actually install. At least you will know if they boot elsewhere, then you can go about figuring out the hardware issue if that's what it ends up being.

---

### Post by rummy77 on 2010-11-30
You might have to tell your BIOS to boot from a CD or flash disk.  If you're not pressing any key when it boots, the BIOS is probably trying to look for a bootloader on you hard disk, which isn't working.  Make sure you're getting the BIOS to boot from the disks, and it should be OK.

---

### Post by kgarbutt on 2010-11-30
There was probably a hidden partition that was deleted by Ubuntu that the Windows CD is looking for. This my guess.

---

### Post by Dans564 on 2010-11-30
are u letting grub load?  Because without some tweaking grub won't boot a cd that is in your cd drive.  You must make sure to enter the BIOS boot selector before Grub can load.  For example, when my computer is turning on I can hold down the F8 key to pick what media BIOS will use to boot your computer,  if nothing is pressed my computer boots Grub like normal then grub boots ubuntu.

---

### Post by Dans564 on 2010-11-30
> **kgarbutt said:**
> There was probably a hidden partition that was deleted by Ubuntu that the Windows CD is looking for. This my guess.

this would make sense if he was using the windoze disk that came with the laptop, cause sometimes they put checks to make sure it is booting the computer it came with.

---

