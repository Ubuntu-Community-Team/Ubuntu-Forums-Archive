---
title: "Liboobs-WARNING mystery"
date: 2009-07-30
forum: General Help
---

### Post by the_family_guy on 2009-07-30
Hi all,

I recently did some manual package installs on my Ubuntu (Oct 2008 version), and now I am getting this error:

foo@foo-laptop:~$ sudo services-admin

(services-admin:6786): Liboobs-WARNING **: There was an unknown error
communicating with the backends: Cannot do system-bus activation with
no user

I went ahead and edited the service file below (added "User=root"), but it only changed the error message....

foo@foo-laptop:~$ sudo gvim
/usr/share/dbus-1/services/org.freedesktop.SystemToolsBackends.service
foo@foo-laptop:~$ sudo services-admin

(services-admin:6753): Liboobs-WARNING **: There was an unknown error
communicating with the backends: Failed to setup environment correctly

Any ideas?

Thanks a ton!
-Peter G.

---

