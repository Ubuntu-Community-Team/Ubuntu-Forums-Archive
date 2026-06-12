---
title: "Access unix media box over network"
date: 2011-12-16
forum: General Help
---

### Post by Jethro_uk on 2011-12-16
I have a cyclone media player on my network. It can happily access samba shares on my 10.04 machine.

Does anyone know if it's possible to get *into* the media player *from* the 10.04 box ? The reason I ask, is I would like to be able to remotely "push" files onto the media player USB drive, rather than "pull" then using the media players TV UI.

I have tried SSHing into it, and FTP and Windows Share (from the Nautilus menu) but no dice. Am I missing something ?

---

### Post by Jethro_uk on 2011-12-16
Oops forgot TELNET (you can tell I'm a windows boy !)

TELNET brings up a login prompt ... only snag - no credentials !!!!!

---

### Post by Jethro_uk on 2011-12-16
OK, things have moved on ... I can now TELNET into the box, and using Nautilus, I can get as far as the password prompt for an SMB share, using the "mygroup" domain.

NOW, the snag is, despite me using the username "guest" and discovering the smb.conf files, I can't access the box ... it acts like the password isn't blank.

Can anyone help further ?

---

### Post by 2F4U on 2011-12-16
If the password isn't published in the documentation it may be hard to find a way in.

---

### Post by Jethro_uk on 2011-12-21
> **2F4U said:**
> If the password isn't published in the documentation it may be hard to find a way in.

here's the smb.conf ... don't appear to have the smbpasswd command 
available 

```
[global]
security=share
log file=/usr/local/samba/var/log.%m
max log size=2000
domain logons=Yes
dns proxy=No
use sendfile=yes
guest account=root
encrypt passwords=yes
passdb backend=smbpasswd
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_SNDBUF=8192 SO_RCVBUF=8192
read raw=yes
write raw=yes
oplocks=yes
max xmit=65535
dead time=15
getwd cache=yes
lpq cache=30
read prediction=yes
client NTLMv2 auth=yes
[C]
path=/tmp/usbmounts/sda1
hide dot files=yes
hide files=/.*/lost+found/
guest ok=yes
writable=yes 
force create mode=0775 
force directory mode=0775 
[D]
path=
hide dot files=yes
hide files=/.*/lost+found/
guest ok=yes
writable=yes 
force create mode=0775 
force directory mode=0775 
```

---

