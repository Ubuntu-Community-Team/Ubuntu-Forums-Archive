---
title: "ltsp: xdmcp not enabled"
date: 2006-01-20
forum: General Help
---

### Post by widulino on 2006-01-20
hi everybody,
tried to setup an ltsp server today.
but after searching these forums for hours without succes one very important failure still remains:
I simply can't log in from a clien, an ltspconfig reveals that xdmcp is not enabled, even though in /etc/gdm/gdm.conf there's
[xdmcp]
enable=true
would be greatful for any hints
widulino

---

### Post by ape on 2006-01-20
Have you restarted the gdm service?  `sudo /etc/init.d/gdm restart`

---

