---
title: "Ubuntu firewall: allow Samba only on private network"
date: 2011-03-19
forum: General Help
---

### Post by Beowolf64 on 2011-03-19
How to configure firewall so that Samba is accessible only to within the private (home) network.

To be more specific, we have a router and several PC connected to that router. All home PCs have private IP addresses 192.168.xxx.xxx.

I tried using Gufw, but couldn't figure out how to limit access to the private network only.

Any help is greatly appreciated. Thank you.

---

### Post by Morbius1 on 2011-03-19
You can do it without a firewall from within Samba itself if you want to:

Add a line to the [global] section of /etc/samba/smb.conf:
```
allow hosts = 127.0. 192.168.
```[COLOR=Blue]*Don't forget the training "." at the end.*[/COLOR]

You can do this globally as I suggested above or by share if your shares are defined in smb.conf - and not created in Nautilus.

[COLOR=Blue] EDIT: Don't forget to restart samba:[/COLOR]
```
 sudo service smbd restart
```

---

### Post by HermanAB on 2011-03-20
Howdy,

Do restrict Samba as explained above, but you also need to filter all the broadcasted cruft from the Windows machines at your LAN router.  So drop these ports: 135 to 139 and 445.

---

