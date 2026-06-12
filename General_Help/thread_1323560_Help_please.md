---
title: "Help please?"
date: 2009-11-11
forum: General Help
---

### Post by CyberRhino on 2009-11-11
Hi there, I'm new to Linux(though so far, I'm 110% glad I made the switch from Windows) but I'm still unsure about a lot of things so far, slowly learning though ;)

Anywho, I've got a quick question, and any help would be appreciated :)

In my System Logs, I'm constantly getting these messages, and I'm not sure what to do about fixing them -->

Nov 11 15:24:51 kevin-desktop kernel: [ 1241.048676] ath5k phy0: noise floor calibration failed (2412MHz)
Nov 11 15:24:51 kevin-desktop wpa_supplicant[1164]: CTRL-EVENT-SCAN-RESULTS 


The first one comes every 10 seconds, and the second one comes every 10 minutes. As far as I can tell, other than this, my system is running fine.

---

### Post by werdberd on 2009-11-11
That second message you're seeing appears to be harmless.  See bug [lpbug]352118[/lpbug] on Launchpad.  Users have reported the first message being associated with their wireless network card dropping connections, but if that isn't happening to you then it may not be a problem.

---

