---
title: "SSH Tunnel For VNC Connection"
date: 2011-11-12
forum: General Help
---

### Post by robn30 on 2011-11-12
I am pretty new to Ubuntu and Linux in general but am making headway figuring things out.  I want to make sure I am doing things right to connect a VNC over a secure SSH Tunnel.  First I am creating the SSH connection by opening a Terminal and entering ssh -L 5900:localhost:5900 host ip.  Of course I then enter the required password and the SSH connection is established.  Next I start x11vnc server using the SSH connection by entering x11vnc -connect "ip of machine performing the help", this then sets up the required vnc-server which is now waiting for a connection.  Last I open Remmina on the machine I have used to establish the SSH connection and enter localhost:5900 in the server box, username, and password, then hit connect and the remote desktop is then displayed.  Is this all correct and do I now have a secure VNC connection?  This is obviously for my local network.  If I wanted to perform these same procedures to help a friend on a different network would the SSH Tunnel look something like this, ssh -R 5900:localhost:5900 user@users externally visable ip?

---

### Post by robn30 on 2011-11-12
Also if someone could help me with the ssh_config editing to use the id_rsa.pub keys to login without passwords to ssh.  Thanks.

---

