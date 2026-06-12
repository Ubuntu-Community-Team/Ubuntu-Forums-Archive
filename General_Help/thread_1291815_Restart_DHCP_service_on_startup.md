---
title: "Restart DHCP service on startup"
date: 2009-10-15
forum: General Help
---

### Post by JimPMM on 2009-10-15
Hi all
New to this forum, and fairly new to Linux so bear with me!
I have Ubuntu running with the DHCP3 service to give out ip addresses on the LAN which it does very well.......as long as I log in as administrator and manually retart the DHCP service after the machine has booted up. The service appears to have started (it's ticked) but no IP addresses are dished out until I restart the service.
Could anyone advise on how to have the service restart automatically once the machine has booted up to login screen as it's causing a few issues! Alternatively, is there something wrong and the service isn't actually running as it should be on startup?
Many thanks
Regards
Jim

---

### Post by justleen on 2009-10-15
make sure there are correct symlinks in /etc/rcx.d. 
If there are no simlinks there to the dhcp server, it wont start at boot.
To update rc.d, you can use ```
 sudo update-rc.d dhcp3-server defaults 
```

---

