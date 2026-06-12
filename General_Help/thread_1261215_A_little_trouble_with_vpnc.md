---
title: "A little trouble with vpnc"
date: 2009-09-08
forum: General Help
---

### Post by oddparticle on 2009-09-08
Hi, I'm hoping this is quite a straightforward problem - I've been trying to connect to my university network using VPNC (which I have done in the past with no trouble, but not since upgrading to Jaunty), and am getting an error message after I've entered all the connection details and passwords, after which the internet doesn't work at all until I tell it to disconnect the VPN. Here's the error message:

resolvconf: Error: /etc/resolv.conf must be a symlink
VPNC started in background (pid: 10290)...

If instead of using the terminal I try to connect using network manager, I instead get an error message saying 'The vpn connection '(null)' failed because there were no valid vpn secrets.'

Thanks in advance for any help :)

---

### Post by oddparticle on 2009-09-08
I've now reinstalled the resolvconf package, and am not getting the error message anymore when using vpnc-connect. However, the internet is still totally failing to work whilst the vpn is supposedly connected. :(

---

### Post by Whiffle on 2009-09-08
Mine was doing something similar, I think it may have something to do with it trying to route *all* traffic through the VPN by default.  I haven't had time to look into it, but thats probably where I'd start looking.

---

