---
title: "Compiz reseting!"
date: 2011-10-14
forum: General Help
---

### Post by SENTINEL5000 on 2011-10-14
Hi to all, I installed Ubuntu 11.10 and been trying for a while to get wobbly windows running, I go to a terminal and run this command:  "compiz --replace &". After running that command wobbly windows effect works but if I restart the PC I have to run the same command again. Is there something I can do for the effect to be permanent? Thanks in advance!

---

### Post by effenberg0x0 on 2011-10-14
Compiz should be enabled by default when, at lightdm, you select the "Ubuntu" session. That means not only wobbly windows but other of COmpiz effects would always be enabled in this session. There would be no need for you to manually launch Compiz the way you're doing.

Now, if you are having problems with the "Ubuntu" session, in which you have no Compiz enabled, no launcher/panel, etc, this is another issue.

When you are in lightdm, make sure to click the small gear icon right next to your name and select the "Ubuntu" session (which uses Compiz). The "Ubuntu 2d" session does not uses Compiz. 


Regards,
Effenberg

---

### Post by SENTINEL5000 on 2011-10-14
Ok I fixed it by adding the command to the startup programs launcher. Thanks anyways!

---

