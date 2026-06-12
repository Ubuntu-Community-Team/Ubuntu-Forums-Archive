---
title: "autostart samba"
date: 2006-03-27
forum: General Help
---

### Post by Tobitas on 2006-03-27
I have to start samba manually by typing ```
sudo /etc/init.d/samba start
``` every time I boot my computer. What do I have to change so samba is started automatically?
Thanks

---

### Post by frodon on 2006-03-27
In System > Administration >  the "Services" window allow you to select which service you want to run on boot or not.

---

### Post by Tobitas on 2006-03-27
Sorry, forgot to mention I am running xfce and not gnome. 
System-Administration does not exist. Is there a comparable tool with this desktop environment, or can I do this alternatively by editing a startup script? 
thanks for the help
Tobias

---

### Post by frodon on 2006-03-27
duh, sorry i didn't see that you are a Xubuntu user.

Maybe you could do that with [BUM]("http://www.marzocca.net/linux/bum.html"), it's in the repositories.

---

### Post by Tobitas on 2006-03-27
Thanks,
installed BUM and changed the boot sequence. Samba is now set to S19, was S20. Not that I really understand what I was doing, but samba seems to start now upon system boot. 
Nice tool
Tobias

---

### Post by tbeehler on 2006-03-28
[QUOTE=frodon]duh, sorry i didn't see that you are a Xubuntu user.

Maybe you could do that with [BUM]("http://www.marzocca.net/linux/bum.html"), it's in the repositories.[/QUOTE]


Perfect!  This is exactly what I was looking for when I was trying to set up another service to auto start.  Thanks!

Travis

---

