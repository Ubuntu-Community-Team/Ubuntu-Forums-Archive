---
title: "network-manager-openvpn not correctly saving configuration"
date: 2010-08-30
forum: General Help
---

### Post by MediocreGopher on 2010-08-30
I've currently got a vpn server running remotely. I have a configuration file called "client.conf" in my home folder. If I do:
```

cd ~
sudo openvpn client.conf

```Then a connection is successfully made and a device called tun0-00 appears in ifconfig. I can also ping other computers on the vpn.

However, when I try to import the configuration file into gnome network-manager, it gets buggy on me. All the keys and certificates show up correctly, but when I hit save and try to connect it gives me an error saying "there were no valid vpn secrets". Looking back at the settings for the connection in network-manager, now all the fields where there are supposed to be the keys are filled with folder names and other random files in my home directory. Resetting the fields doesn't help, as saving the configuration just re-jumbles them.

Does anyone have any idea how to fix this?

Kernel: 2.6.32-24-generic
OS: Ubuntu 10.04

---

