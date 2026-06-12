---
title: "Connection timed out/no route to host"
date: 2010-12-05
forum: General Help
---

### Post by JustSteph on 2010-12-05
Hi, when trying to run "sudo /usr/share/doc/libdvdread4/install-css.sh", I'm getting the error:

```

--2010-12-05 14:47:43--  http://packages.medibuntu.org/dists/lucid/free/binary-i386/Packages
Resolving packages.medibuntu.org... 88.191.127.22
Connecting to packages.medibuntu.org|88.191.127.22|:80... failed: No route to host.
Dynamic fetch failed; Falling back to static fetch
--2010-12-05 14:47:52--  http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_i386.deb
Resolving packages.medibuntu.org... 88.191.127.22
Connecting to packages.medibuntu.org|88.191.127.22|:80... failed: Connection timed out.
Retrying.

--2010-12-05 14:48:14--  (try: 2)  http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_i386.deb
Connecting to packages.medibuntu.org|88.191.127.22|:80... failed: No route to host.p
```

I applied the proxy system-wide in the preferences, but is this still the cause of the problem? If so, how can I fix it?

Thanks
Steph

---

