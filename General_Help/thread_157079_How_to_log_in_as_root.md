---
title: "How to log in as root?"
date: 2006-04-08
forum: General Help
---

### Post by priyaaank on 2006-04-08
I am newbie to ubuntu and linux. And though I gathered the idea that there is no "specific" root login in ubuntu... but suppose I wanted to open fstab file in rw mode, in my GUI editor and not in console... How do I do that??

I mean, in console I could say sudo vi fstab... so it is rw mode
but as a user, which even belongs to root group, I do not have write access to fastab when I open it in editor...

will chmod of fstab file from sudo account help?? Though I really don't want that... I want some other permanent solution which I am sure, I am not aware of, as if now.. 
Help me stumble my way around.. I really want to adapt! :D

---

### Post by localzuk on 2006-04-08
In order to edit a file as 'root', you need to run the command in sudo mode. So, for instance, sudo gedit /etc/fstab would open gedit to edit /etc/fstab.

Do this on a terminal.

---

### Post by dave9191 on 2006-04-08
You can get a root terminal with 

sudo -s

for the root shell from any terminal window.

--
Dave

---

### Post by qamelian on 2006-04-08
Just use the 'sudo' command to gain temporary root access.
For example, 

```
sudo gedit /etc/fstab
``` 
and enter your own password when prompted.

---

### Post by verbalshadow on 2006-04-08
this wiki doc explains about sudo and setting the root password if you still feel you need it after reading it.

[RootSudo]("https://wiki.ubuntu.com/RootSudo")

---

### Post by Donnut on 2006-04-08
You can log in as root, but it isn't a very good idea, the security of linux depends on this very simple limitation.

---

