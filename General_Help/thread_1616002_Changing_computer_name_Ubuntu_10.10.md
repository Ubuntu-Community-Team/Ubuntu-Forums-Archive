---
title: "Changing computer name Ubuntu 10.10"
date: 2010-11-07
forum: General Help
---

### Post by JudeaB on 2010-11-07
How do I change my computer's name in Ubuntu 10.10 with minimal distress to installed programs, pls?  Enjoying getting back to some command line ops after Windows 7 but still taking it slowly! :-)  Thanks for any help, Jude

---

### Post by hakermania on 2010-11-07
I think you have to edit /etc/hostname
give to a terminal
sudo gedit /etc/hostname
type your preferable name and save the file. open a new terminal to see if it works (it will say yourname@NEWhostname:)

---

### Post by ajgreeny on 2010-11-07
> **hakermania said:**
> I think you have to edit /etc/hostname
give to a terminal
sudo gedit /etc/hostname
type your preferable name and save the file. open a new terminal to see if it works (it will say yourname@NEWhostname:)
Then reboot, or you may experiece the odd problem.

---

### Post by efflandt on 2010-11-07
Replies forgot something else essential.  Besides editing **/etc/hostname** you also have to change the name in **/etc/hosts**.  Otherwise your computer may not be able to find itself the next time it boots.

---

### Post by JudeaB on 2010-11-07
> **efflandt said:**
> Replies forgot something else essential.  Besides editing **/etc/hostname** you also have to change the name in **/etc/hosts**.  Otherwise your computer may not be able to find itself the next time it boots.


:-)  Thks for help.  B.t.w edited as per original suggestion and computer rebooted and seems happy with apps.  However following suggestion edited /etc/hosts and rebooted.  Still happy so ty.  Cheers, :)

---

