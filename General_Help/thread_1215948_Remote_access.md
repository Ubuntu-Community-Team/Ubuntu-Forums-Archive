---
title: "Remote access?"
date: 2009-07-17
forum: General Help
---

### Post by Colo2 on 2009-07-17
Hello, I need to remotely help my friend who is new to ubuntu. On windows, I used to use teamviewer but on linux, it seems the only alternative is VNC. I like VNC, but it involves forwarding ports which unfortunatly isn't possible.

Is there a teamviewer equivilant which doesn't envolve forwarding ports?

Thanks  :popcorn::D

---

### Post by t4thfavor on 2009-07-17
There are pay for use remote desktop viewers that work on linux, but they will most likely cost too much.

I'm afraid without frwarding ports on his side you cannot get into his machine, unless the router has upnp.

---

### Post by Colo2 on 2009-07-18
Alright, thank you for the reply :) I will get him to forward port.

JUst out of interest. what port(s) need to be forwarded for VNC server?

---

### Post by TuckLive on 2009-07-18
Default port is 5900, but I think you have the option to change it easily.

---

### Post by Colo2 on 2009-07-18
Thank you :)

---

### Post by XCan on 2009-07-18
> **TuckLive said:**
> Default port is 5900, but I think you have the option to change it easily.

The setting for port number was removed in the 'normal' Remote Desktop setting windows. You can find it in "gconf-editor -> desktop -> gnome -> remote_access"

---

### Post by The Cog on 2009-07-18
If you don't mind him connecting to you with SSH, then you could have him SSH to your machine like this:
ssh -R5900:127.0.0.1:5900 user@ipaddress
The -R argument will make VNC connections to your machine get forwarded to his machine without him having to forward any incoming ports. This will be more secure for him than having his VNC open to the internet.

Edit:
Then you just VNC to your own machine 127.0.0.1 and you will find yourself talking to his.

---

