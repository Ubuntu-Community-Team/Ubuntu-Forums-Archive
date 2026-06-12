---
title: "Synaptic and all other UI tools do not open with sudo, gksu"
date: 2011-12-05
forum: General Help
---

### Post by EReckase on 2011-12-05
I have a fresh build of 11.04 that somehow has gotten into a configuration where no window applications will open when using sudo or gksu, including synaptic.  I get the following error:

g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.

There's nothing in the various system logs to indicate any reason for this failure.  I get this error both sitting in front of the machine and through NX, but if I remote the display with ssh -Y, it works.

Any ideas?  I'm at a total loss.

---

