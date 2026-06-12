---
title: "Connecting into Windows Remote Desktop ?"
date: 2011-07-22
forum: General Help
---

### Post by albertwt on 2011-07-22
Hi People,

Is it possible from Ubuntu Linux to remote desktop into any Windows Server through RDP ?

I've tried using TightVNC it works from within the internal LAN but this is connecting from my home PC with Ubuntu over CISCO VPN client.

Thanks,
Al

---

### Post by MDguy on 2011-07-22
Did you try using Terminal Server Client?  It comes with Ubuntu by default, and should be under Applications-->Internet on the Gnome desktop.  If you are using Unity, you can search for it in the Dash, or type
```
tsclient
```
in the terminal.

---

### Post by varunendra on 2011-07-22
> **MDguy said:**
> Did you try using Terminal Server Client?  It comes with Ubuntu by default, and should be under Applications-->Internet on the Gnome desktop.  If you are using Unity, you can search for it in the Dash, or type
```
tsclient
```in the terminal.
+1
I keep doing this all the time using tsclient.

**EDIT:**
Oh, I missed the 'VPN' part. Haven't tested it for VPN yet.

---

### Post by cybergalvez on 2011-07-22
> **albertwt said:**
> Hi People,

Is it possible from Ubuntu Linux to remote desktop into any Windows Server through RDP ?

I've tried using TightVNC it works from within the internal LAN but this is connecting from my home PC with Ubuntu over CISCO VPN client.

Thanks,
Al

I personally like Remmina, it does RDP and VNC

---

### Post by ingramproductions on 2011-07-22
```
rdesktp *server_name/ip*
```

---

