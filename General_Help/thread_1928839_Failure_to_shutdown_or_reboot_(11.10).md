---
title: "Failure to shutdown or reboot (11.10)"
date: 2012-02-20
forum: General Help
---

### Post by enpey on 2012-02-20
Hi All,


Since a fresh install of 11.10 (64 bit), the system does not shutdown or reboot (longest it has been left is overnight). Until I purged modemmanager, the processes were stopping on "modem-manager[xxx]: <info> Caught signal 15, shutting down... [fail]" or similar. It is now coming to "Killing all remaining processes... [fail]" or similar (since purging modemmanager).

I have tried to purge/remove NetworkManager and network-manager but my system becomes unuseable and I am seemingly unable to do this. As soon as I hit "sudo purge network-manager", access to the web dissappears (e.g. ping [www.yahoo.com](www.yahoo.com) results in "unknown host" response from system).

dmesg results attached.


Any help will be greatly appreciated,
enpey

---

### Post by enpey on 2012-02-21
Reinstalled and purged network-manager first boot.

Using wired connection instead of wireless now also (saw some suggestions that wpa-supplicant may be misbehaving - but I don't know).

---

