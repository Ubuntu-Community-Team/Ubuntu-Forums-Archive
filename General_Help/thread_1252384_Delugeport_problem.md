---
title: "Deluge/port problem"
date: 2009-08-28
forum: General Help
---

### Post by codered1444 on 2009-08-28
how com deluge says no incomming connections when the ports are open in the router an

---

### Post by fatbotgw on 2009-08-28
It's probably because the port is closed on your system's firewall.  Try installing firestarter from the repositories and opening the port up.

---

### Post by lovinglinux on 2009-08-28
> **fatbotgw said:**
> It's probably because the port is closed on your system's firewall.  Try installing firestarter from the repositories and opening the port up.

There is no need to install Firestarter just to do that. You can clear the firewall rules with the command below:

```
sudo iptables -F
```

To check if you actually have any rules:

```
sudo iptables -L
```

But keep in mind that if you didn't create any rules, then all ports are already opened, since Ubuntu accept all connections by default.

Are you able to connect to any peers? 
Are you sure the port is forwarded to the correct internal IP of your machine?
Have you configured Deluge to use the same port forwarded by the router?
Have you checked if the torrent tracker is online and you are connecting to it?

---

