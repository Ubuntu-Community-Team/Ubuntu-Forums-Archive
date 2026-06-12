---
title: "Recover boot"
date: 2010-07-09
forum: General Help
---

### Post by aletof on 2010-07-09
Hi!

I had a working dual Win 7-Ubuntu on a Gateway laptop. Somehow the computer wouldn't get past the BIOS verification into the GRUB.

I used the Ubuntu Live CD and managed to use Gparted to delete my Ubuntu installation, I left the Windows and Gateway recovery partition untouched but still the computer won't get to the point where I can restore the system using the Gateway Win7 partition, which I need to do in order to keep my Win7 license/installation (Gateway doesn't include recovery CD's).

Is there a way to get that working from the Ubuntu LiveCD?

Thanks in advance for your help!

---

### Post by garvinrick4 on 2010-07-09
> **aletof said:**
> Hi!

I had a working dual Win 7-Ubuntu on a Gateway laptop. Somehow the computer wouldn't get past the BIOS verification into the GRUB.

I used the Ubuntu Live CD and managed to use Gparted to delete my Ubuntu installation, I left the Windows and Gateway recovery partition untouched but still the computer won't get to the point where I can restore the system using the Gateway Win7 partition, which I need to do in order to keep my Win7 license/installation (Gateway doesn't include recovery CD's).

Is there a way to get that working from the Ubuntu LiveCD?

Thanks in advance for your help!
Boot off of Ubuntu and Use Try Ubuntu (live cd) and copy and paste
these 2 lines of code in a Terminal. Should put a boot back into Windows.
                                 

Restore basic windows boot loader - universe enabled
```
sudo apt-get install lilo
``````
sudo lilo -M /dev/sda mbr
```May show error messages about the rest of lilo missing, ignore, we just want MBR



Also check into seeing if your Windows 7 does not let you make disk's (3 of them dvd)
for your install. And you can make recovery disks, all you want if cannot find google there is a site.

---

### Post by aletof on 2010-07-10
Lilo made it work perfectly, Thanks! :D

I'll look into creating the backup DVD's!

---

