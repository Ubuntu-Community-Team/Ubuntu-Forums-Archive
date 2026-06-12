---
title: "There were no valid vpn secrets error from NetworkManger"
date: 2010-09-06
forum: General Help
---

### Post by hq4ever on 2010-09-06
Hi,

I'm running ubuntu 10.04, Gnome.

```
uname -a
Linux maximveksler-desktop 2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:21:58 UTC 2010 x86_64 GNU/Linux

```

I've installed NetworkManager vpnc plugin
```
aptitude install network-manager-vpnc-gnome
```

Then I configured NetworkManager using the GUI: Network Connections, VPN > Add > "Choose a VPN Connection Type" = Cisco Compatible VPN (vpnc)...

Yet when I try to connect using network manager I get the error "The VPN Connection 'XYZ' failed because there were no valid VPN secrets".

I can verify that the vpn connection works and the settings are correct because droping to root shell and calling vpnc directly does work.

```
root@maximveksler-desktop:~# vpnc --gateway xzy.company.com --id XYZGROUP --username maxim.veksler
```

What am I doing wrong? Is there a log for NetworkManager? 
I should say that this is pretty much vanilla installation of Ubuntu...

Thank you,
Maxim.

---

### Post by hq4ever on 2010-09-06
It seems that 

```
sudo restart network-manager
``` Solves the problem. Yet this seems like a bad design decision... User should not be aware that he needs to restart the network-manager daemon for his settings to take affect.

---

