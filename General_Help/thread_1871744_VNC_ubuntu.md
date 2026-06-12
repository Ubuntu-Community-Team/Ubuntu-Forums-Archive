---
title: "VNC ubuntu"
date: 2011-10-29
forum: General Help
---

### Post by x84n on 2011-10-29
I am running ubuntu 10.04 64bit and I want to connect using vnc, currently using ssh to do stuff on there, I was lloking to install the vnc server but it says I have to do it through GNOME how do I install gnome then connect to it?

---

### Post by Lars Noodén on 2011-10-29
Look at the package tightvncserver that will install without Gnome.

---

### Post by x84n on 2011-10-29
Do you have a link please to download.

---

### Post by Dangertux on 2011-10-29
I would highly recommend sticking to SSH. Particularly if this is going to be accessible from the Internet.

If you MUST manage via VNC over the internet do it through a VPN, and manage it locally from the VPN. VNC is one of the easiest remote administration services to be cracked and is frequently the cause of "I got hacked" posts on this forum.

If you still want to install tightvncserver the following should work for you.

```

sudo apt-get install tightvncserver

```Hope that helps.

EDIT : that should have read VNC is easy to crack not VPN thanks CharlesA for the correction.

---

### Post by Lars Noodén on 2011-10-29
To add what Dangertux wrote, it goes without saying that VNC should not be used alone and should be tunneled.  A VPN is usually overkill and it is enough to simply [tunnel VNC over SHH](https://help.ubuntu.com/community/VNC#SSH_port-forwarding).

---

