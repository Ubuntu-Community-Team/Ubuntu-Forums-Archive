---
title: "Connection problem"
date: 2010-09-07
forum: General Help
---

### Post by Steam. on 2010-09-07
I use ubuntu 10.04, and i have a router now.When i tried to go through the DSL connection(i had a switch first), it worked(with the router).Next time i booted it up, no connection works.On windows it connects automatically to the internet because of the router, but here it doesn't even budge.Anyone?

---

### Post by Steam. on 2010-09-07
Anyone?

---

### Post by Steam. on 2010-09-10
Oh come on, does anyone know how to help?

---

### Post by aeiah on 2010-09-10
are you using dhcp? you can check in your network settings..


at the terminal, try
```

sudo dhclient
```

that should give you a new dhcp lease. perhaps you've got a static ip set but your subnet has changed. maybe in windows you have dhcp so it gets assigned a new IP, but in ubuntu its still trying to set a now forbidden IP.

---

### Post by Steam. on 2010-09-11
That worked, thanks.And i don't have a static IP.

---

