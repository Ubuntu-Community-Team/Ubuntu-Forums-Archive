---
title: "Can't install ms TrueTrye fonts."
date: 2011-05-21
forum: General Help
---

### Post by Wilf999 on 2011-05-21
I'm trying to install the ms True type fonts on 11.04.

I typed the command:      "sudo apt-get install ttf-mscorefonts-installer"

And, after a short wait the following screen appeared (added as an attachment)

And - I'm stuck.  I can scroll up or down through the EULA with my scroll wheel or the arrow keys, but I cannot move on, I can't click on the OK, and no keypress does anything.

I tried to remove the installer with:    "sudo apt-get remove ttf-mscorefonts-installer" and with the Ubuntu software center and both operations failed.  The terminal advised me to reinstall before removal, which I can't.

Please Help

Thanks in advance

Wilf

---

### Post by aeronutt on 2011-05-21
When I install this through synaptic, a pop-up comes up with a radio button to accept the licence agreement.  Might try that. UPDATE: on second thought, it was when I installed ubuntu restricted extras from synaptic, which include ms fonts. So, try ms fonts in synaptic, and if that doesn't work, you could try restricted extras.

---

### Post by coffeecat on 2011-05-21
When you install something through the terminal and get a EULA to OK , press the tab key to move the highlight to the OK. Then enter should accept the OK.

---

### Post by Wilf999 on 2011-05-21
Solved this by running Update Manager.

This produced an error message telling me I needed to do a partial upgrade, which fixed the incorrectly installed package, and gave me a nice GUI interface to approve the EULA.  Too used to Windows I'm afraid.

Thanks for the advice everyone.

Wilf

---

### Post by Arbayong on 2011-06-15
Thanks Coffeecat. Your method worked. I had this problem for more than a week. after reading your message, i pressed tab and then the ok key and all ways ok. once again, Thanks very much

---

