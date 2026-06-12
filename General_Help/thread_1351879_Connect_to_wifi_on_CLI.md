---
title: "Connect to wifi on CLI"
date: 2009-12-11
forum: General Help
---

### Post by pencilpenpen on 2009-12-11
____

---

### Post by pencilpenpen on 2009-12-14
___

---

### Post by NoBugs! on 2009-12-15
If you run the "nm-applet" command does the network-manager icon show up? Does it give error message?

---

### Post by Isengrin on 2009-12-15
Is netcfg in the repos? it's what I use in Arch for connecting via CLI. Good and easy to use.
Just put a file in /etc/network.d called whatever you like, and call it with ```
netcfg filename
```

Here is an example of the file:
```
CONNECTION="wireless"
DESCRIPTION="Isengrin's Lunaris network"
INTERFACE="wlan0"
HOSTNAME="luna"
IP="dhcp"
IFOPTS="dhcp"
SECURITY="wep"
ESSID="Lunaris"
KEY="1122334455"
SCAN="no"
```

Just change your description (can be whatever you like), hostname, ESSID and key. =)

---

### Post by aplonis on 2012-10-05
On Ubuntu 12.04 LTS I find no path /etc/network.d into which to add such a file.

Does this method still work for 12.04 LTS? Or does it simply go into a different path?

---

### Post by nothingspecial on 2012-10-05
Please start a new thread. This one is old and rather mouldy.

Closed.

---

