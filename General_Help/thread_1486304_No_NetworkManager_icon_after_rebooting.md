---
title: "No NetworkManager icon after rebooting"
date: 2010-05-17
forum: General Help
---

### Post by Fibonacci on 2010-05-17
Hello.

I've noticed that there's no Network Manager icon on my notification area after rebooting, no matter how many times I delete my GNOME panel configuration and restore the defaults.
However, after rebooting, if I restart the D-Bus service (and thus my whole desktop), the NM icon does appear - even though NetworkManager is not running.
I've already tried reinstalling gnome-panel, network-manager, and dbus, which hasn't changed anything.

How can I make the NM icon appear every time I log in?

---

### Post by Fibonacci on 2010-05-18
Bump.

---

### Post by Super_Dork_42 on 2010-08-05
> **WorMzy said:**
> To reset the panels. In a terminal write:

```
mkdir ~/.oldpanel
```then
```
mv ~/.gconf/apps/panel ~/.oldpanel
```then
```
*gconftool-2 --shutdown*
```finally
```
pkill gnome-panel
```NOTE: This will completely reset your  panels to the default configuration, they will look the same as if you'd  done a fresh install.

There you go. Tested it so it works and isn't malicious code.

---

### Post by david_cuenca on 2010-08-06
Thanks Super_Dork_42 that worked for me!

---

### Post by Super_Dork_42 on 2010-08-07
You're welcome. The reason I found your thread is because I had the same problem. So, I posted what I found that worked for me.

---

