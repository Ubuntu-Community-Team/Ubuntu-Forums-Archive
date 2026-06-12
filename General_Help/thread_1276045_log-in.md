---
title: "log-in"
date: 2009-09-26
forum: General Help
---

### Post by toolmanpaul on 2009-09-26
how do i log in as root...what the root password?

---

### Post by overdrank on 2009-09-26
> **toolmanpaul said:**
> how do i log in as root...what the root password?

Hi and I think [RootSudo]("https://help.ubuntu.com/community/RootSudo") should help.

---

### Post by toolmanpaul on 2009-09-27
i dont like the default page for abiword.(the reason for the root question) file name is normal.awt and when i open and edit the way i like ...i can't save it..says u don't have permission......still hav not found the secret to edit and save this default start page for abiword. again the page name is normal.awt....it's properties are read only execpt as root, then they  are w / r ...i don't know how to edit as root   can someone help? thsnks!!

---

### Post by Joeb454 on 2009-09-27
To edit it with root privileges, what I would recommend is the following (replace 'gedit' with the name of the text editor you want to use)

```
gksu gedit /path/to/normal.awt
```

Not forgetting to replace /path/to/normal.awt with the actual file system path ;)

---

### Post by grturner on 2009-09-27
in ubuntu, the root account is actually disabled.
To access a root terminal you can do
sudo -i 
or
sudo bash

the root account is disabled as a security feature, though we are unable to tell you how to enable it due to the forum policies. Of course there's always google.

---

