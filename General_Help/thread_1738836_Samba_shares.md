---
title: "Samba shares"
date: 2011-04-25
forum: General Help
---

### Post by Sanix on 2011-04-25
Hi, I've got some questions regarding samba shares.

I shared a folder using nautilus. Where can I review the configuration. I tried to locate the shares in
/etc/samba/smb.conf but they're not there. So I'm wondering, how and where does nautilus create these shares?

When I allow guest access. And a folder is created using this guest access, there's always no owner and no group assigned to it. How can I specifiy the default user und which those folders should be created? Is it also possible to set defaults rights (like 755)?

---

### Post by collisionystm on 2011-04-25
> **Sanix said:**
> Hi, I've got some questions regarding samba shares.

I shared a folder using nautilus. Where can I review the configuration. I tried to locate the shares in
/etc/samba/smb.conf but they're not there. So I'm wondering, how and where does nautilus create these shares?

When I allow guest access. And a folder is created using this guest access, there's always no owner and no group assigned to it. How can I specifiy the default user und which those folders should be created? Is it also possible to set defaults rights (like 755)?

If you are looking for these features without getting to in depth, just install webmin.

You can add a share, set the username, group etc... and permission level all in 2 clicks.

It is web based, so just fire up your webbrowser after install, localhost:10000

---

### Post by Sanix on 2011-04-25
Thanks. But even this tool can't see the shares created by Nautilus. So I wonder, how it's done there.

---

