---
title: "eth0 Disabled,How to enable?"
date: 2011-04-23
forum: General Help
---

### Post by OohRahh on 2011-04-23
Hello, I am new to Ubuntu. I installed the server version 10.04. The only problem with the install was setting up the network.
I believe it was due to the fact that my nic was not setup correctly. The installation reconciled the nic, but upon the reboot after the install, I had no network capabilities. I tried to ping the router, no luck. ifconfig only showed lo.

Also, the GUI (command F7) freezes and does not responds. The last thing shown is configuring web server. 

I tried to ndsiwrapp the drivers to the nic, but found out that ndsiwrapper is for wifi connections. Any suggestion on getting the nic to work?

---

### Post by debd on 2011-04-23
Try this:
Enter the below code in a terminal, you'll be asked for your account password;

```
gksu gedit /etc/network/interfaces
```

and make sure the file only contains these two lines:

```
auto lo
iface lo inet loopback
```

---

### Post by grahammechanical on 2011-04-23
You can try

```
sudo ifup eth0
```

regards.

---

