---
title: "Samba Users- How Do You Edit Your Setup?"
date: 2011-05-20
forum: General Help
---

### Post by Roasted on 2011-05-20
Hey thar Samba users. How do you go about editing your shares, users, etc.? I'm curious what other users are doing.

Any system-config-samba users out there? Simple yet very effective gui tool that directly alters smb.conf. I used it to learn. I would make changes in the gui and then read the smb.conf to see what changed.

There's also GAdmin-Samba, SWAT, Zentyal, Webmin and of course old faithful, sudo gedit /etc/samba/smb.conf. Is there anything else I missed that's effective?

---

### Post by bdoe on 2011-05-20
I use SWAT. It's been a very effective tool for me to remotely manage Samba on my headless server.

---

### Post by Roasted on 2011-05-21
Is SWAT still supported and developed for? I thought I remember hearing people say use Webmin instead of SWAT, but now that Webmin is "incompatible" with Ubuntu (yet it somehow works with all other Linux distros) it makes me wonder.

---

### Post by Roasted on 2011-05-23
anybody else?

---

### Post by CharlesA on 2011-05-23
I set my users up with smbpasswd. :)

That said, I only have 3 users to set up.

I've used webmin in the past, and I tried using SWAT, but it was a bit confusing for me.

---

