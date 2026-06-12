---
title: "problems with package requirement for dbus-glib-1"
date: 2012-06-16
forum: General Help
---

### Post by OccamsChainsaw on 2012-06-16
I am trying to install dbus-python-1.0.0. When I try to configure, I get the following error:

```
configure: error: Package requirements (dbus-glib-1 >= 0.70) were not met:

No package 'dbus-glib-1' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables DBUS_GLIB_CFLAGS
and DBUS_GLIB_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```I wasn't able to find a package specifically titled 'dbus-glib-1', so I installed dbus-glib (v 0.92-5) and libdbus-glib-1-2 (v 0.94-3) which sounded very similar to what dbus-python needed.  But the config still fails with the same error.

So my question is, what is the relationship between dbus-glib and dbus-glib-1 packages, if they're not the same thing? and if dbus-glib does have the python bindings i need, what do i need to do with the configure script so it recognizes this? Thanks in advance.

---

### Post by OccamsChainsaw on 2012-06-17
bump

---

### Post by OccamsChainsaw on 2012-06-18
I don't know what that's supposed to mean, and I think you be spammin'. But thanks for the bump.

---

