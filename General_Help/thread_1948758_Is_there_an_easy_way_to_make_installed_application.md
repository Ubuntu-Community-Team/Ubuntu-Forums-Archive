---
title: "Is there an easy way to make installed applications available for other users?"
date: 2012-03-28
forum: General Help
---

### Post by BurakUeda on 2012-03-28
Hi,

Finally, I have decided to move away from using ubuntu as root and created an account with admin privileges. But when I logged in, it was a totally different world. Dozens of applications and their customized settings were gone (of course).

Is there any way to make the applications I have installed as root available for the admin user?
Or do I need to install and configure them again?

Thanks...

---

### Post by JC Cheloven on 2012-03-28
Ubuntu is designed to use the 'sudo' command to achieve administrative privileges when needed, NOT a root account. 

In fact talking about root account how-to is somehow against the CoC of the forums. 

If you use the regular procedure, all installed programs will be automatically available to the users.

Thanks
JC

---

### Post by cariboo on 2012-03-28
You could copy/move the configuration files from /root to /home/$USER. You will more than likely have to change the ownership to your user name.

---

### Post by jerome1232 on 2012-03-28
> **cariboo907 said:**
> You could copy/move the configuration files from /root to /home/$USER. You will more than likely have to change the ownership to your user name.

+1, per user configurations are stored in that users home, so it should be as simple as copying roots home to your user then recursively chowning your users home to get ownership.

---

### Post by BurakUeda on 2012-03-28
@JC, point taken. That is why I am quitting using root.

@jerome & cariboo, thank you. Moving files and changing permissions seems to be working.

---

