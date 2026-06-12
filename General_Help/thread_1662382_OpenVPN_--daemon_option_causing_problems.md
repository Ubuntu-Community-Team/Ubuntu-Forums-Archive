---
title: "OpenVPN --daemon option causing problems"
date: 2011-01-08
forum: General Help
---

### Post by icedown on 2011-01-08
I'm trying to get openvpn to start as a service.  I can get it to work easily by running 
```
/usr/sbin/openvpn --config /etc/openvpn/sgs.conf
```

but when I try to start it using the service, it shows that it starts.  It shows up in ps but the tun device is not created.  Can't seem to find any log entries from it either.  Here is the command line it uses

```
/usr/sbin/openvpn --writepid /var/run/openvpn.sgs.pid --daemon ovpn-sgs --status /var/run/openvpn.sgs.status 10 --cd /etc/openvpn --config /etc/openvpn/sgs.conf --script-security 2

```

If I remove the --daemon option, it works just fine.  Any ideas?

---

