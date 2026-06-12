---
title: "Control (REAL) Daemons KDE"
date: 2010-01-30
forum: General Help
---

### Post by markinf on 2010-01-30
Anyone knows where I can control daemons startup on KDE? On systemsetting there is only KDE daemons, I want to control startup of crond/mysqld/apache2d and son on.

I want something like this from Gnome
[IMG]http://blog.ubuntu-tweak.com/wp-content/uploads/2007/09/services-of-ubuntu.png[/IMG]

---

### Post by Zorael on 2010-01-30
In a sense that falls outside of KDE's domain as an environment.

You can install the Boot-up Manager (package name **bum**) to manage this. It's a GTK app, so it's not KDE per se. It will also look ugly as sin when run as root.

If you want a terminal tool, **sysv-rc-conf** is also in the repositories.

---

### Post by markinf on 2010-01-30
> **Zorael said:**
> In a sense that falls outside of KDE's domain as an environment.

You can install the Boot-up Manager (package name **bum**) to manage this. It's a GTK app, so it's not KDE per se. It will also look ugly as sin when run as root.

If you want a terminal tool, **sysv-rc-conf** is also in the repositories.

So only GNOME has this tool, KDE doesn't? Thats really irritating, KDE not having a Boot/Daemons service control. I like KDE a lot but it's hard to love something thats doesnt have the same tools in completude compared to GNOME.

---

### Post by bs27975 on 2011-04-10
> **Zorael said:**
> In a sense that falls outside of KDE's domain as an environment.

That may be, but it is not out of the realm of kubuntu.

---

