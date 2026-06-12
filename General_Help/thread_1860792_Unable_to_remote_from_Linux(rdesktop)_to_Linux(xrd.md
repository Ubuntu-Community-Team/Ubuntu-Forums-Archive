---
title: "Unable to remote from Linux(rdesktop) to Linux(xrdp)"
date: 2011-10-15
forum: General Help
---

### Post by SteveDee on 2011-10-15
I'm probably being very dim here, but don't know how to remotely access one 'buntu machine from another using rdp.

From a terminal I run:-
```

rdesktop -u steve  192.168.0.10

```
...and get a "Login to xrdp" dialog.

Using the default "sesmanXvnc" gives me a connection, but the window is just grey with an X mouse curser. I can move the cursor, but there is nothing to select.

Using "sesman X11rdp" I get "error-only supporting 8 or 16bpp rdp connections"

The other options don't work for me either. Which option should I be using?

I have been using VNC between these 2 machines for a couple of years. But I've recently been playing with rdesktop between 'buntu & Windows and it works great, and much faster than VNC.

So can anyone talk me through this?

---

### Post by dcstar on 2011-10-15
> **SteveDee said:**
> I'm probably being very dim here, but don't know how to remotely access one 'buntu machine from another using rdp.

From a terminal I run:-
```

rdesktop -u steve  192.168.0.10

```
...and get a "Login to xrdp" dialog.

Using the default "sesmanXvnc" gives me a connection, but the window is just grey with an X mouse curser. I can move the cursor, but there is nothing to select.

Using "sesman X11rdp" I get "error-only supporting 8 or 16bpp rdp connections"

The other options don't work for me either. Which option should I be using?

I have been using VNC between these 2 machines for a couple of years. But I've recently been playing with rdesktop between 'buntu & Windows and it works great, and much faster than VNC.

So can anyone talk me through this?

Just tried to use RDP to my 10.04 test system, similar problems to you.

---

