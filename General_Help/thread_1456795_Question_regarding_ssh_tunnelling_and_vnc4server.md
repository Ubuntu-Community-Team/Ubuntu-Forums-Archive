---
title: "Question regarding ssh tunnelling and vnc4server"
date: 2010-04-17
forum: General Help
---

### Post by MalcolmIan on 2010-04-17
I have what I think is a dead simple question, but it's been vexing me.  I've searched this question quite a bit, but I can't seem to get anything, so I think I am probably misunderstanding the issue.

I have a headless box running Karmic.  I installed the vnc4sever and set up the server with the configuration file below.  I have ssh server set up on the box and I can successfully connect to the VNC client using an ssh tunnel.  My problem is that access is not restricted to port forwarding.  I can VNC my way in to port 5901 from anywhere without an ssh tunnel.

I'm sure I'm missing something completely obvious here, but how do I restrict access to only ssh tunnels?

/etc/xinetd.d/Xvnc
```
service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
        server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/fonts/X11/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd -extension XFIXES
        port = 5901
}

```

---

### Post by gmargo on 2010-04-17
Two possible solutions come to mind:
1. Use a firewall to block the port from the network interface.
2. Use the 'bind' parameter in your xinetd file to only bind to the localhost address.

---

