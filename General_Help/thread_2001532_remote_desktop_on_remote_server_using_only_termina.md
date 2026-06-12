---
title: "remote desktop on remote server using only terminal"
date: 2012-06-11
forum: General Help
---

### Post by Forux on 2012-06-11
Is it possible to configure remote desktop on remote server using only terminal?

on server (ubuntu 11.10 server), i can access it using ssh (seperuser available)

Thank for any help!

---

### Post by roelforg on 2012-06-11
Look up ssh tunneling

---

### Post by codemaniac on 2012-06-11
Have you already installed Openssh server on the remote server you want to access using terminal ?

[https://help.ubuntu.com/10.04/serverguide/openssh-server.html](https://help.ubuntu.com/10.04/serverguide/openssh-server.html)

---

### Post by roelforg on 2012-06-11
> **codemaniac said:**
> Have you already installed Openssh server on the remote server you want to access using terminal ?
 
[https://help.ubuntu.com/10.04/serverguide/openssh-server.html](https://help.ubuntu.com/10.04/serverguide/openssh-server.html)
 
The OP said (and i quote):
> 
i can access it using ssh (seperuser available)

So i thing he can.

---

### Post by codemaniac on 2012-06-11
Thanks roelforg , just missed out on that .

---

### Post by roelforg on 2012-06-11
[https://help.ubuntu.com/community/SSH/OpenSSH/PortForwarding](https://help.ubuntu.com/community/SSH/OpenSSH/PortForwarding)
 
You could, in theory, tunnel a vnc connection over ssh. Though it's easier and faster to have individual programs connect back using X11-tunneling if you only plan on using one or two programs (it would be a bit wasteful on both speed and remote resources to tunnel a whole desktop for 1 program).

---

