---
title: "Squid does not start after boot"
date: 2010-05-19
forum: General Help
---

### Post by mehturt on 2010-05-19
After upgrade to 10.04 squid does not start automatically after boot.  Starting it manually via:
sudo start squid
works fine.

---

### Post by mehturt on 2010-08-09
Nobody else seeing this?

What's strange to me, the /etc/init/squid.conf contains:

start on (filesystem
        and net-device-up IFACE!=lo)

While /etc/init/ssh.conf contains:

start on filesystem

And ssh starts fine after boot.

---

### Post by Xerophie on 2010-11-10
also happened to me, I use maverick & after a power failure the box automatically boot up through the bios setting (power on after power failure) but Squid does not run automatically, its run normally after doing command **sudo start squid** or **reboot** once more.

:confused:

---

