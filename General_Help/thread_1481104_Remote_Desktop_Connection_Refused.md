---
title: "Remote Desktop Connection Refused"
date: 2010-05-12
forum: General Help
---

### Post by rapidvelo on 2010-05-12
I've enabled Remote Desktop on Ubuntu 10.04, however when I attempt to connect from a Windows 7 machine to the Ubuntu PC it keep getting connection refused.
 
I rebooted Ubuntu after setting the remote desktop settings, still without any luck.
 
Anyone have any ideas?
 
Thank you!

---

### Post by Ryan Dwyer on 2010-05-12
I don't think the Windows Remote Desktop client will work. You need to download VNCviewer for Windows.

---

### Post by rapidvelo on 2010-05-12
> **Ryan Dwyer said:**
> I don't think the Windows Remote Desktop client will work. You need to download VNCviewer for Windows.
 
Yes sorry I should have mentioned, I tried with RealVNC and TightVNC still nothing.   I even added :0 at the end of the IP without any luck.

---

### Post by cdenley on 2010-05-12
```

sudo netstat -tlnp
gconftool -R /desktop/gnome/remote_access

```

---

### Post by rapidvelo on 2010-05-12
> **cdenley said:**
> ```

sudo netstat -tlnp
gconftool -R /desktop/gnome/remote_access

```

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      838/cupsd       
tcp6       0      0 :::5900                 :::*                    LISTEN      1232/vino-server
tcp6       0      0 ::1:631                 :::*                    LISTEN      838/cupsd       
thomas@MEDIA-UBU:~$ gconftool -R /desktop/gnome/remote_access
 icon_visibility = client
 vnc_password = 
 authentication_methods = [vnc]
 network_interface = 
 require_encryption = false
 disable_background = false
 enabled = true
 use_alternative_port = false
 mailto = 
 disable_xdamage = false
 lock_screen_on_disconnect = false
 view_only = false
 prompt_enabled = false
 alternative_port = 5900
 use_upnp = true

---

### Post by cdenley on 2010-05-12
The server is listening for connections. If you're getting "connection refused", then it is either a networking problem, or it is being filtered by a firewall.
```

sudo iptables -L -n

```

---

