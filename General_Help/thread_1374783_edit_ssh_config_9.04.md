---
title: "edit ssh_config 9.04"
date: 2010-01-07
forum: General Help
---

### Post by mr_wonderful_ on 2010-01-07
hello all, 

quick questions, Im trying to control my works server from home (due to the snow) and need to edit part of my monte carlo code so need Xforwarding turned on, have tried to edit /ect/ssh/ssh_config to this effect but Im being told I do not have the permission to save the editted file... I am the only user on the computer and this is a pretty much fresh copy of Ubuntu (using 9.04 instead of 9.10 due to networking issues on my laptop, didnt want to risk it on my desktop) Im still pretty fried from new year so cant function and figure out how to fix it :-)

please point me in the right directions

cheers

Nick

---

### Post by webwiz on 2010-01-07
most files in /etc/ need root permission to edit the files
If you are the only user on the box, you probably have sudo permission.  

from a terminal type:  sudo nano /etc/ssh/sshd_config

---

### Post by mr_wonderful_ on 2010-01-07
thats magic thank you :-)

---

### Post by Iowan on 2010-01-07
Personally, I like **nano**, but if you'd prefer a graphical editor, the command would be:```
gksudo gedit /etc/ssh/sshd_config
```

---

### Post by bodhi.zazen on 2010-01-07
use 

```
sudo -e /etc/ssh/ssh_config
```

If you do not like nano, set root's environmental variable (EDITOR) to gedit

---

### Post by Iowan on 2010-01-07
> **bodhi.zazen said:**
> ```
sudo -e /etc/ssh/ssh_config
```
I'd forgotten this handy shortcut since last time you posted it... 
Unfortunately, I'll probably forget it again.

---

### Post by bodhi.zazen on 2010-01-07
> **Iowan said:**
> I'd forgotten this handy shortcut since last time you posted it... 
Unfortunately, I'll probably forget it again.

:lolflag:

---

