---
title: "Can't bring up my networking screen"
date: 2006-02-01
forum: General Help
---

### Post by gwash on 2006-02-01
System->administration->Networking

I see a box open on the bottom saying 'starting networking' but then it disappears and nothing shows up.

I'm having a problem getting my internet to work via ethernet and I thought that screen would help me figure my problem.

any help would be appreciated

thanks

---

### Post by gruepig on 2006-02-02
I'm not sure why the Networking utility disappears, but ....

You can configure the network from the command line/terminal.  Most network settings are in the file /etc/network/interface.  Are you using DHCP?  If so, you just need something like:

```

auto eth0
iface eth0 inet dhcp

```

Then run 'sudo ifup eth0' to try bringing up your network interface.  Use 'ifconfig -a', 'route -n', and 'cat /etc/resolv.conf' to view your current network configuration.  If you have a specific problem with your network, it would be helpful to post the output of those three commands.

Browse around or ask if you need more clarification.

---

