---
title: "Administrator Access Help!"
date: 2011-03-31
forum: General Help
---

### Post by galacticaboy on 2011-03-31
I am running Xubuntu 10.04, how do I get it to stop asking me for my password every time I go to install something or do anything that needs Administrator access? There has to be a way, it sorta reminds me of Windows Vista (*shudders*) with all of the "Password" and "Are you sure" prompts. How can I stop it.

---

### Post by Rubi1200 on 2011-03-31
If you want to install software and you know it will take longer than the default 15 minutes timeout for sudo, try ```
sudo -i
``` in a terminal; this grants you temporary root privileges for the duration of the session and don't forget to exit when you are done.

As far as the comparison with Vista is concerned, I only have this to say:

The security mechanisms in Windows are tacked on stop-gap methods with no real thought given to the usage and security of the system. 

Linux on the other hand employs a model of security which has been there since the beginning; it is tried and tested and guarantees that you will have a safe and secure computing experience.

---

### Post by rubylaser on 2011-03-31
You'll need to edit your /etc/sudoers file.  Open a terminal, and type this in.
 ```
sudo gedit /etc/sudoers
```

And change the line with your username to look like this...
```
username   ALL=(ALL) ALL, NOPASSWD: /usr/sbin/synaptic
```
username above represents your username.  This will leave the rest of root user security in place, but prevent you from having to enter your password to work with Synaptic. Hope that helps.

---

### Post by Rubi1200 on 2011-03-31
> **[COLOR=Red]Because sudo is such a powerful program you must take  care not to put anything formatted incorrectly in the file. To prevent  any incorrect formatting getting into the file you should edit it using  the command visudo run as root or by using sudo. [/COLOR]**
**[COLOR=Red]sudo visudo[/COLOR]**
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

---

### Post by galacticaboy on 2011-03-31
Well if it can harm my system, i think I will pass. I do not want to do that! Thanks anyway guys!

---

