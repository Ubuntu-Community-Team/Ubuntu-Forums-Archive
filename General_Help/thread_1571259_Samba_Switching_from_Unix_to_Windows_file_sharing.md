---
title: "Samba: Switching from Unix to Windows file sharing"
date: 2010-09-09
forum: General Help
---

### Post by General_Zero on 2010-09-09
I'm using [https://help.ubuntu.com/10.04/internet/C/networking-shares.html](https://help.ubuntu.com/10.04/internet/C/networking-shares.html) to help set up my server for windows file sharing. I accedently pressed unix file sharing and now i can switch it to windows file sharing.

it would be fine to uninstall the Unix file sharing and replace it with the windows counterpart.

I have Ubuntu desktop 10.04 (because i keep getting an error with the kernel with the server editions) if you can help me with that problem also it would be very helpful also(just PM me).

---

### Post by Morbius1 on 2010-09-09
There seems to be some debate on this ( actually only by one persion so far ) but shares-admin as in ( from the HowTO ):
> Type **shares-admin** and press **Enter** to open **Shared Folders**.is broke.

What you need is the following package:
```
system-config-samba
```If samba is not installed it should install it.

To access it:

Administration > Samba

OR

gksu system-config-samba

---

