---
title: "How To configure Synaptic (apt-get) through a proxy"
date: 2006-06-19
forum: General Help
---

### Post by lauro.sa on 2006-06-19
**There are 2 ways:**

**1st. **Configure your synaptic (apt-get) proxy settings:

 a. Return your /etc/apt/apt.conf to the original:

*Acquire::http:Proxy "False";*

 b. In *Synaptic/Preferences/Network* type:

Manual Proxy:
Proxy HTTP: *user:Passw@proxy*       PORT: *port*
Proxy FTP:  *repeat*

 c. In *System/Preferences/Network Proxy* type:

*Direct Connection*

 With this, http_proxy variable will be blank and it will not confuse your Synaptic.

-------------------------------------------------------------

**2nd.** Configure your network proxy settings (http_proxy variable):

 a. Return your */etc/apt/apt.conf* to the original:

*Acquire::http:Proxy "False";*

 b. In *System/Preferences/Network Proxy* type:

Manual Proxy:
Proxy HTTP: *user:Passw@proxy*       PORT: *port*  DETAILS: *put user and passw again*
Proxy HTTPs:  *repeat*
Proxy FTP:  *repeat*
Host Socks:  *repeat*

 This works because the **http_proxy variable is mandatory **to Synaptic (apt-get).
 **[COLOR="Red"]The problem of this option is[/COLOR]**: with the command "echo $http_proxy" users can see your passw.

-------------------------------------------------------------

---

