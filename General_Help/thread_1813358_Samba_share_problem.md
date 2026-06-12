---
title: "Samba share problem"
date: 2011-07-27
forum: General Help
---

### Post by nidzo732 on 2011-07-27
I have two computers(desktop and laptop) and a router. The desktop is conected with router via LAN cable and the laptop connects via wifi. They both have samba installed. I have some files on the desktop that i want to access from laptop. But when i try to connect i get this:
```
nidzo@nidzo-lt:~$ smbclient //192.168.1.2/share -U nidzo
Enter nidzo's password: 
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.5.8]
tree connect failed: NT_STATUS_BAD_NETWORK_NAME
```

192.168.1.2 is the ip adress of the desktop.

---

### Post by kerry_s on 2011-07-27
Did u try from nautilus?

---

### Post by nidzo732 on 2011-07-27
Yes, laptop doesn't see the desktop.

---

### Post by kerry_s on 2011-07-27
are you sure the desktop folder is shared? did you right click the folder-> share

i'm using lubuntu, so my setup is different.

---

