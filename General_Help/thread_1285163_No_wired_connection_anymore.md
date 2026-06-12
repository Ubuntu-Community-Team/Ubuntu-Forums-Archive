---
title: "No wired connection anymore"
date: 2009-10-07
forum: General Help
---

### Post by gyan on 2009-10-07
Hello.
I have some issues setting up a pppoe conection on my ubuntu 9.04 operatins system.

The provider's instructions were to run a script that run these two lines:
```

route del -net 10.0.0.0 netmask 255.0.0.0

route add -net 10.0.0.0 netmask 255.0.0.0 gw 10.22.0.1

```

I was receiving error messages like:
```

SIOCADDRT: No such process

```
then tried to enter the lines manualy, i guess it worked.

I configured the connection using pppoeconf(typed username and password +enter ...).

That worked for the moment, but at the next restart, my wired internet connection was not found (a red X at the top right over the networking applet).

Tried a lot of things but my unexperience made me call it a day.

I dual boot between xp and ubuntu, and i can say the internet connection is running fine on xp.

Is someone willing to help me fix this issue on ubuntu?

Thanks.

---

