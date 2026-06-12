---
title: "Network folder"
date: 2011-07-15
forum: General Help
---

### Post by Uzi304 on 2011-07-15
Ok so there's this particular folder I want to get into on Linux and on Windows I would just type in: ```
\\folderName
``` in the addressbar of Windows Explorer. Now for this particular folder I would need to sign into the school's VPN while on Windows. Does anyone know how I'd be able to do this on Linux, more specifically on KDE if that helps. Thanks

---

### Post by btindie on 2011-07-15
You'll first need to install a VPN client and confirm that the connection works.

If it's a Cisco VPN then you just need to install vpnc and also a plugin for NetworkManager that allows you to configure it through that. I don't use KDE so it might differ slightly as to what application you need. But from doing a quick search I found that there's a KDE specific VPN client front end or you could use the network-manager plugin for KDE
```
user@linux:~$ apt-cache search vpnc
kvpnc - vpn clients frontend for KDE4
kvpnc-data - data files for KVpnc
kvpnc-dbg - vpn clients frontend for KDE4 - debugging symbols
network-manager-vpnc - network management framework (VPNC plugin)
network-manager-vpnc-gnome - network management framework (VPNC plugin, GNOME UI)
network-manager-vpnc-kde - KDE NetworkManagement infrastructure (VPNC plugin)
vpnc - Cisco-compatible VPN client

```Set up your VPN connection and verify that it works by pinging a know host.

Open your file manager and go to the network places, again this'll vary. Under nautilus you can just press Ctrl+L then type in the URL
```
smb://ServerName/FolderName
```Also under nautilus, and I dare say under dolphin(?), on the file menu there's a Connect To Server option where you can specify the details.

If you haven't used Samba on your computer before then you may need to install some additional packages.

---

### Post by KeyserSoze93 on 2011-07-15
KDE uses the KIO slave smb:// to access windows shares. Try navigating to smb:/ and you should see the windows shares on your lan.

If it's a hidden then, then try something like "smb://server/share"

---

### Post by Uzi304 on 2011-07-15
How can I tell what kind of VPN it is?

---

### Post by btindie on 2011-07-18
They should have provided you with the logon details for the VPN along with what client you need to use to connect to it. Did they give you a link to download the Cisco VPN client??

---

