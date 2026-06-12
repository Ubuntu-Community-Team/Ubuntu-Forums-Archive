---
title: "cannot resume for hibernation/standby"
date: 2010-07-10
forum: General Help
---

### Post by Cfhs_1 on 2010-07-10
Well, the title basically says it all. On my Desktop machine (Dell Dimension 4600) When ubuntu goes into standby or hibernation and I wake it up, the system seems to resume okay, but I don't get any video output. My monitor (HP w2338h) says there is no signal coming from the computer, and since it's kinda hard to use a computer with no video I'm forced to power it off and reboot. I'm using a Nvidia GeForce 5200 Graphics card with my HP w2338h monitor. I was hoping this would be fixed with updates, but it's been a while now and this still isn't fixed. Can someone please help me? I like using the standby and hibernation features, so simply not using them won't work. Thanks in advance!

---

### Post by robsoles on 2010-07-11
The graphics controller is the only thing we need focus on, in my opinion anyway.

Are you using proprietary drivers? does 'lspci' in terminal list the card correctly? Is there anything else about this video card or the way you use it that might be relevant?

---

