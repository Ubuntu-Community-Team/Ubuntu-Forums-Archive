---
title: "Samba Reinstall Problems"
date: 2012-04-11
forum: General Help
---

### Post by caspertk on 2012-04-11
Could somebody please help me with a reinstall issue. I installed samba through the terminal and was configuring. (using this guide: [https://help.ubuntu.com/11.04/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/11.04/serverguide/C/samba-fileserver.html)) I messed up configuration, didn't know how to fix it so I uninstalled, and reinstalled. It still had the messed up configuration so I purged and uninstalled and manually deleted from /etc. Now upon install no folders or files installed in /etc, and when I type samba in the terminal it says that it's not installed i can install it by... yet when i do so, it says it's already installed.

Any help is appreciated. Thanks in advance.

---

### Post by Morbius1 on 2012-04-11
/etc/samba/smb.conf does not come from the "samba" package. It comes from the "samba-common" package because smb.conf is used by both the samba client and the server.

You should have a copy of it already installed at [B]/usr/share/samba/smb.conf

[/B]Just copy it over to /etc/samba

---

### Post by caspertk on 2012-04-11
Yeah that worked. Thanks!

---

