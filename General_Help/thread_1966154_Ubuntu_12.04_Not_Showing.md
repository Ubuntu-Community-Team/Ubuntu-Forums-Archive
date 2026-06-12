---
title: "Ubuntu 12.04 Not Showing"
date: 2012-04-26
forum: General Help
---

### Post by Ubun2to on 2012-04-26
I want to be able to boot Ubuntu 12.04 from my laptop, but it won't show up (although it does take me to the select OS screen now).
I'm using Windows 8 developer preview on my laptop, as this thing is junk, and I test whatever I want to on it before I put it on my main computer.
My guess is that Wubi isn't writing the Ubuntu option to the Master Boot Record (MBR) properly in Windows 8, but I'm not too sure right now.
Also, I usually just download the live DVD, as it comes prepackaged with everything on it, but they haven't uploaded it yet, so I'm using Wubi.
Please help.

---

### Post by dcstar on 2012-04-28
> **Ubun2to said:**
> I want to be able to boot Ubuntu 12.04 from my laptop, but it won't show up (although it does take me to the select OS screen now).
I'm using Windows 8 developer preview on my laptop, as this thing is junk, and I test whatever I want to on it before I put it on my main computer.
My guess is that Wubi isn't writing the Ubuntu option to the Master Boot Record (MBR) properly in Windows 8, but I'm not too sure right now.
Also, I usually just download the live DVD, as it comes prepackaged with everything on it, but they haven't uploaded it yet, so I'm using Wubi.
Please help.

AFAIK Win 8 uses the non-BIOS booting and requires tweaks to allow Linux to boot. You may need to check the Grub HOWTOs.

---

