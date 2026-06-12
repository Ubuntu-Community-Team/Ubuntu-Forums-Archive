---
title: "Root User"
date: 2010-01-31
forum: General Help
---

### Post by nmyrick on 2010-01-31
I am having trouble editing my /etc/laptop-mode/conf.d/battery-level-polling.conf file when I am logged in as root, or any other user.  My permissions are set to let the root user have read and write priveledges, but I am getting the following error when trying to open this file through the terminal as the root user:

[COLOR="DarkRed"]root@laptop1:~# /etc/laptop-mode/conf.d/battery-level-polling.conf
-bash: /etc/laptop-mode/conf.d/battery-level-polling.conf: Permission denied
root@laptop1:~# 
[/COLOR]

[COLOR="Black"]The reason I am trying to edit this file is that when my computer gets to critical battery level, it just shuts off and does not hibernate.  I would like to change the "Enable_Battery_Level_Polling value to "1", in order to correct this.  The value is currently set to "0".

Can anyone help me with this?

Thanks,
nmyrick[/COLOR]

---

### Post by rogue_0111 on 2010-01-31
> **nmyrick said:**
> 

[COLOR=DarkRed]root@laptop1:~# /etc/laptop-mode/conf.d/battery-level-polling.conf
-bash: /etc/laptop-mode/conf.d/battery-level-polling.conf: Permission denied
root@laptop1:~# [/COLOR]
[COLOR=Black]
Can anyone help me with this?

Thanks,
nmyrick[/COLOR]


[COLOR=DarkRed]root@laptop1:~# sudo /etc/laptop-mode/conf.d/battery-level-polling.conf[/COLOR]

---

### Post by nmyrick on 2010-01-31
I tried entering sudo, but that did not work.  I get the following error.

[COLOR="DarkRed"]nmyrick@laptop1:~$ sudo -i
[sudo] password for nmyrick: 
root@laptop1:~# sudo /etc/laptop-mode/conf.d/battery-level-polling.conf
sudo: /etc/laptop-mode/conf.d/battery-level-polling.conf: command not found
root@laptop1:~# [/COLOR]

---

### Post by wojox on 2010-01-31
Get out of root and try this:

```
gksudo gedit /etc/laptop-mode/conf.d/battery-level-polling.conf
```

---

### Post by mprokolo on 2010-01-31
what he wrote

---

### Post by nmyrick on 2010-01-31
Thank you Wojox, that worked.  Now I just hope that changing that value fixes my problem, I read in a different post that it would.

nmyrick

---

