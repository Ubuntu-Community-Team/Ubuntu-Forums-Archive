---
title: "Network manager from CLI"
date: 2009-08-13
forum: General Help
---

### Post by poisonkiller on 2009-08-13
Hello!
I've been trying to get network manager to autoconnect VPN on login (via nm-applet), but it doesn't seem to work. So, after a while I found this command: /usr/lib/network-manager-pptp/nm-pptp-auth-dialog -u <UUID> -n <network name> -s org.freedesktop.NetworkManager.pptp
My question is, where can I find a VPN's UUID?

---

### Post by michy99 on 2009-08-13
If you run```
sudo blkid
```while connected to the VPN, does it show the UUID?

---

### Post by poisonkiller on 2009-08-13
No, it only shows sda1, sda5 and sda6 UUID's.

---

### Post by michy99 on 2009-08-13
What do you get for```
ls /etc/NetworkManager/system-connections/
```

---

### Post by poisonkiller on 2009-08-13
> **michy99 said:**
> What do you get for```
ls /etc/NetworkManager/system-connections/
```
It displayed "Auto eth0". So I sudo nano'd it, got eth0's UUID and tried it in the command. It worked, asked my password, but then froze. I think that program was only a password dialog and there must be something else to connect the VPN... Please, does somebody have a good idea how to make VPN autoconnect?

---

### Post by poisonkiller on 2009-08-14
Anybody?

---

