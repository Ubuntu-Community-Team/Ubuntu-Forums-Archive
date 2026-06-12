---
title: "Attempting to install open vpn"
date: 2012-07-25
forum: General Help
---

### Post by jlapinski4 on 2012-07-25
I am attempting to install open VPN and I get this ```
 jeffrey@Ubook31A:~$ cd /etc/apt/sources.list.d
jeffrey@Ubook31A:/etc/apt/sources.list.d$ wget http://repos.openvpn.net/repos/apt/conf/repos.openvpn.net-precise-snapshots.list
--2012-07-25 20:04:13--  http://repos.openvpn.net/repos/apt/conf/repos.openvpn.net-precise-snapshots.list
Resolving repos.openvpn.net (repos.openvpn.net)... 173.192.237.102
Connecting to repos.openvpn.net (repos.openvpn.net)|173.192.237.102|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 70 [text/plain]
repos.openvpn.net-precise-snapshots.list: Permission denied

Cannot write to `repos.openvpn.net-precise-snapshots.list' (Permission denied) 
```

Any help is appreciated!

---

### Post by Cheesehead on 2012-07-25
openvpn is in the Ubuntu repos, did you try that one?```
sudo apt-get install openvpn
```

If you're sure you want to run the upstream version instead of the Ubuntu version, then take a look at the /etc/apt/sources.list.d permissions. Your user has permission to see it, but not to save to it. Add sudo to the command, and it should work.

---

### Post by jlapinski4 on 2012-07-26
That wasn't working last night (I did try) but tonight it did work.  One day I will figure this Linux - thing out!

Thank you!

---

