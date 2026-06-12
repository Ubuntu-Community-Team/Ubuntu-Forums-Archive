---
title: "proxy from GUI Apps not working"
date: 2006-03-17
forum: General Help
---

### Post by General Moskovich on 2006-03-17
I have two Ubuntu Breezy systems. I've installed ntlmaps on one
(10.4.5.80). My /etc/bash.bashrc file (on the other system) looks like the
follow:

export http_proxy=http://10.4.5.80:5865

This works great from the command line, but doesn't work from any GUI
application (Synaptic, Firefox, etc...).

I have configure the proxy settings in all the GUI applications to use
10.4.5.80 and port 5868 as my proxy.

Any ideas what I'm doing wrong?

Thanks!

Mosko

---

### Post by dcstar on 2006-03-17
[QUOTE=General Moskovich]I have two Ubuntu Breezy systems. I've installed ntlmaps on one
(10.4.5.80). My /etc/bash.bashrc file (on the other system) looks like the
follow:

export http_proxy=http://10.4.5.80:5865

This works great from the command line, but doesn't work from any GUI
application (Synaptic, Firefox, etc...).

I have configure the proxy settings in all the GUI applications to use
10.4.5.80 and port 5868 as my proxy.

Any ideas what I'm doing wrong?

Thanks!

Mosko[/QUOTE]

System-Preferences-Network Proxy

---

### Post by dcstar on 2006-03-17
[QUOTE=General Moskovich]I have two Ubuntu Breezy systems. I've installed ntlmaps on one
(10.4.5.80). My /etc/bash.bashrc file (on the other system) looks like the
follow:

export http_proxy=http://10.4.5.80:5865

This works great from the command line, but doesn't work from any GUI
application (Synaptic, Firefox, etc...).

I have configure the proxy settings in all the GUI applications to use
10.4.5.80 and port 5868 as my proxy.

Any ideas what I'm doing wrong?

Thanks!

Mosko[/QUOTE]
System-Preferences-Network Proxy

---

### Post by General Moskovich on 2006-03-18
Thanks for the reply but I got that one, too. Any other ideas?

---

### Post by lamego on 2006-03-18
There is no global way to define a application proxies, the http_proxy is a common setting for the console apps and the gnome settings for gnome apps.
For any other application it may used one of this proxy config places or have its own configuration, like firefox, gaim, etc.
This is a problem common on linux/windows apps .

---

