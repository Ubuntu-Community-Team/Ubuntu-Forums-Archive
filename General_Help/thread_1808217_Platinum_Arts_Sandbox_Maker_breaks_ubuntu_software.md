---
title: "Platinum Arts Sandbox Maker breaks ubuntu software center"
date: 2011-07-20
forum: General Help
---

### Post by Niocora on 2011-07-20
OK, so. Using the Ubuntu software center, until just now, I could download fine. Then, I tried to install Platinum Arts sandbox Maker using the Ubuntu software center, it downloaded, then it froze on applying the changes, yet it installed properly. I then tried rebooting and downloading a program using the terminal and it told me
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 


So I obediently did as told and it re-downloaded the program but it still doesn't work. If I reboot, I can install one program and it will stay on the installing screen but really be installed. However, I cannot use the terminal, because of the error. I tried uninstalling Platinum Arts Sandbox Maker but it wouldn't uninstall.

I really need help quickly,

Niocora.

---

### Post by Niocora on 2011-07-20
Anyone at all?

---

### Post by jerrrys on 2011-07-20
i am not finding this package.  how/where did you download from?

---

### Post by knukles141 on 2011-07-21
Yeah i'm having the same problem, any solutions?
I found it browsing the games/rpg section in the software manager.

---

### Post by Niocora on 2011-07-23
Fixed, thanks to josh 443 for having the same problem,

To fix, enter in a terminal.

sudo bash

*enter root password here

apt-get remove sandboxgamemaker


Then enter Y for yes and your done!

---

