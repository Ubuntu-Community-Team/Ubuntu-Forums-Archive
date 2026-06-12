---
title: "building networkmanager from source"
date: 2006-03-06
forum: General Help
---

### Post by zachtib on 2006-03-06
I'm trying to build the latest networkmanager, and ./configure exits fine, but make outputs this:

```
In file included from applet.c:56:
applet-notifications.h:29: error: syntax error before ‘NotifyUrgency’
applet.c:389:40: error: macro "g_return_if_fail" passed 2 arguments, but takes just 1
applet.c: In function ‘nma_show_vpn_failure_dialog’:
applet.c:389: error: ‘g_return_if_fail’ undeclared (first use in this function)
applet.c:389: error: (Each undeclared identifier is reported only once
applet.c:389: error: for each function it appears in.)
applet.c:390:38: error: macro "g_return_if_fail" passed 2 arguments, but takes just 1
make[4]: *** [nm_applet-applet.o] Error 1
make[4]: Leaving directory `/home/zach/build/NetworkManager-0.6.0/gnome/applet'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/zach/build/NetworkManager-0.6.0/gnome/applet'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/zach/build/NetworkManager-0.6.0/gnome'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/zach/build/NetworkManager-0.6.0'
make: *** [all] Error 2

```

what should i do? id be happy to post debs once i get this working

---

### Post by bugmenot on 2006-03-06
removing -Werror and -Wshadow from configure.in should do it.

---

### Post by zachtib on 2006-03-06
[QUOTE=bugmenot]removing -Werror and -Wshadow from configure.in should do it.[/QUOTE]

that made it install, but it doesn't work.  no big deal, ill use 5.x for now, and give 6.0 a try once dapper comes out

---

