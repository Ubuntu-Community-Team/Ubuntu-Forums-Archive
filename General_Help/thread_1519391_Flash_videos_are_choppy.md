---
title: "Flash videos are choppy"
date: 2010-06-28
forum: General Help
---

### Post by GoldDragon on 2010-06-28
When I upgraded to Lucid, I had a problem with sound cutting off after a few minutes of flash usage. I was running 64bit flash, after some instructions I got here I removed 64bit flash and used Flash-aid to install flash. 
The problem I am having now is the video is really choppy, like freeze frame. Any ideas on how I can fix this?
I have tried uninstalling and reinstalling firefox and flash. I have also tried 
> sudo mkdir /etc/adobe
echo "OverrideGPUValidation=true" >~/mms.cfg
sudo mv ~/mms.cfg /etc/adobe/
nothing has worked so far.
Could it be my video card? ( I noticed it doesn't appear to be supported by the drivers that come with Ubuntu ). Should I remove the drivers that came with ubuntu and install the proprietary? I'd really like to get this solved and everything working fine again.. I didn't have these problems before Lucid.
I also have PCLOS installed on a different system and flash works perfectly on it.

---

### Post by Linuxforall on 2010-06-28
Unless you have nvidia or particular ATI card, you can't install proprietary drivers. What you can try is turn off desktop effects to see if this issue goes away.

---

### Post by GoldDragon on 2010-06-28
I have an ATI Radeon HD 3450. The desktop effects are off, so it's not that.

---

