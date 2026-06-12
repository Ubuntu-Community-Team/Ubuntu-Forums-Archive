---
title: "give sudo permission to obmenu?"
date: 2009-11-20
forum: General Help
---

### Post by treehouse on 2009-11-20
I have the openbox menu on my gnome desktop. I want to add shutdown and restart options to my menu using the 'shutdown -h now' command, but it requires root access. How do I make this work without having to put in my password every time I want to halt or reboot?

---

### Post by urukrama on 2009-11-21
Have a look at the Openbox guide linked to in my signature. This is discussed there (section 13).

---

### Post by Prodigal Son on 2009-11-21
/etc/sudoers ( append ):

```
%admin ALL=NOPASSWD: /sbin/shutdown

```

---

### Post by SuperSonic4 on 2009-11-21
```
sudo EDITOR=nano visudo
```

add in either (or both) of the following ```
user ALL=NOPASSWD: /sbin/shutdown #This is for your user to shutdown
#Replace user with your username
```

```
%group ALL=NOPASSWD: /sbin/shutdown #This is for groups, ensure your user is part of the group
#An example group would be %admin, %wheel or %power
```


Press ctrl+X to quit nano and press Y to save changes

---

