---
title: "Vpn"
date: 2010-01-19
forum: General Help
---

### Post by phoenixfire900 on 2010-01-19
is it possible to use a VPN to connect from my computer to a VPN server without using another client computer? in other words is it possible to use a VPN with only one computer?

---

### Post by kdaemon on 2010-01-19
Yes it is possible, at least I have done it in Windows just for testing but why would you want to for practical purposes?

---

### Post by phoenixfire900 on 2010-01-19
which software is best for it?

---

### Post by bodhi.zazen on 2010-01-19
> **phoenixfire900 said:**
> which software is best for it?

OpenVPN

It is a bit of an overkill though as OpenVPN is intended to encrypt traffic over the internet.

On a LAN use some other protocol such as NFS or Samba or if you want encryption sshfs.

---

### Post by phoenixfire900 on 2010-01-19
can i use this for games?

---

### Post by kdaemon on 2010-01-19
Dont think he wants to VPN over the lan, he wants to vpn to the same machine he's on?

---

### Post by kdaemon on 2010-01-19
Setup your box to accept VPN as detailed here:

[http://forums.bit-tech.net/showthread.php?t=132029](http://forums.bit-tech.net/showthread.php?t=132029)

The right click network manager applet to configure a VPN connection using either local host or loop back IP address (127.0.0.1)

---

### Post by bodhi.zazen on 2010-01-19
> **phoenixfire900 said:**
> can i use this for games?

What are you wanting to do exactly ?

---

### Post by cgb on 2010-01-19
It's a little confusing on what you are trying to accomplish.  yes you can connect to a VPN server with just one computer but the point of connecting to a VPN server is so that you can access a remote Network securely and gain access to remote files.  If there is no other computer going to be active on that network then there really is not much of a point.  Unless something is being lost in translation and we probably need more clarification as to what you are trying to accomplish.

---

### Post by phoenixfire900 on 2010-01-19
i got it thanks guys

---

