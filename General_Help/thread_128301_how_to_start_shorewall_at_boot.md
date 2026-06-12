---
title: "how to start shorewall at boot?"
date: 2006-02-11
forum: General Help
---

### Post by shams2 on 2006-02-11
hi, 
i installed the shorewall, how i configure ubuntu to start the shorewall at boot time, in other linux distros like fedora and mandriva one can add to chkconfig then it will start at boot but i didn't find chkconfig in ubuntu can any one tell me what is  the replacement for it?

---

### Post by Rhawi Dantas on 2006-02-11
Once configured, 

sudo gedit /etc/default/shorewall
change STARTUP_ENABLED=Yes.
exit the editor.

reboot your PC.
check the boot up screen file and /var/log/messages and /var/log/shorewall-init.log

;)

---

