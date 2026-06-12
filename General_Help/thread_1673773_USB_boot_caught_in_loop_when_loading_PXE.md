---
title: "USB boot caught in loop when loading PXE"
date: 2011-01-22
forum: General Help
---

### Post by Jonesy_sa on 2011-01-22
Hi all,
I am having issues loading Ubuntu 10.10 from USB. I have a HP Compaq nx9110 laptop, p4 3.2 512ram etc with a dead hard drive. I would buy a new HDD but i cant really vouch spending $80Aus on a IDE 2.5 just to play with linux.
Anyhow it seems to read the USB stick which was created following the directions on this site but when it attempts to load the Realtec LAN (i think) it seems to get stuck in a loop.
I have attached a screen print of what i see, it hangs for a few seconds then starts over with the same writing. Anyone know what that means or how i can fix this so i can try 10.10?
thanks

---

### Post by slooksterpsv on 2011-01-22
You should be able to go into your BIOS and disable PXE, it doesn't look like it's even attempting to boot from USB (or just yet), so I think for HPs its F1... I could be wrong, but press F1, go to a tab that should say like system or security, there will be a networking or pxe option... It's been so long with HPs I don't know exactly. I'll post this, research it and see if I can find out how to do it for you ok?

---

### Post by Jonesy_sa on 2011-01-23
The reason I thought it loads USB is because if I haunt selected boot from USB I don't get this screen plus it occurs not long after the loading light on the USB flashes. I had a look in the bios and could not see a setting to disable pcs or disable network. I can't be the only one that's had this issue... Cheers all

---

