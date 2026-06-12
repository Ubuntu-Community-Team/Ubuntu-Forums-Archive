---
title: "Dual Booting on Two Drives"
date: 2010-05-12
forum: General Help
---

### Post by aunchaki on 2010-05-12
I've got an older PC running Windows 2000. I put a second drive in and installed Ubuntu 9 on it. When booting, the Ubuntu drive booted first and I could mount the Win2K drive for access to data. If I needed to boot into Windows, I just shut down, unplugged my Ubuntu drive and restarted. No worries.

I just did the Ubuntu 9->10 upgrade. It ran into some troubles (GRUB), which I finally got sorted out. I can boot again, BUT the process gorked the MBR on my Windows drive. Ack! Now, when I try to boot from it (Ubuntu drive unplugged), I get a GRUB error message.

So, I can try to repair/restore the MBR on my Win2K drive OR I can figure out how to get GRUB (on the Ubuntu drive) to boot Win2K from the second drive. I think I'd rather get GRUB working, so I don't have to manually unplug stuff.

Any ideas on how to make this happen?

Thanks in advance!

Michael

---

### Post by linuxman94 on 2010-05-12
Could you please run this script and post the RESULTS.txt file?  Be sure to use code tags.

[Boot Info Script]("http://bootinfoscript.sourceforge.net/")

---

### Post by NissanSkylineN1 on 2010-05-12
Well I'm pretty sure that GRUB is recorded ON the MBR. I think thst it first boots from the primary master, and then the master tells its primary slave to boot GRUB. So, I'm guessing that since your Primary Master does not have an MBR, it automatically goes for the second priority. But you have no MBR, so the GRUB gets ignored and Ubuntu loads. A possible solution is to create a HDD image and then fix your HDD. Then once fixed, load the m=image... but 'm not sure if the image includes an MBR.

---

### Post by linuxman94 on 2010-05-12
> **NissanSkylineN1 said:**
> Well I'm pretty sure that GRUB is recorded ON the MBR. I think thst it first boots from the primary master, and then the master tells its primary slave to boot GRUB. So, I'm guessing that since your Primary Master does not have an MBR, it automatically goes for the second priority. But you have no MBR, so the GRUB gets ignored and Ubuntu loads. A possible solution is to create a HDD image and then fix your HDD. Then once fixed, load the m=image... but 'm not sure if the image includes an MBR.

GRUB may have been installed on a partition by accident.  That's why I asked for the result of the script.

---

### Post by aunchaki on 2010-05-14
While my problem persists (gorked MBR of Windows drive), a solution has presented itself.

Originally (after installing Ubuntu 9), when presented with the GRUB boot menu, if I selected the "Windows 2000" boot option, it would NOT boot Win2K (giving me some NTLDR error).

I tried it again last night, just for kicks. It worked!

So, while I cannot boot my Win2K drive all by itself at the moment, I can boot either drive from GRUB now. This is a fine solution, and I'm not worrying about this for a while.

Thanks for all your posts. I'll run the script above ASAP (just to see what it says) and post the results.

---

