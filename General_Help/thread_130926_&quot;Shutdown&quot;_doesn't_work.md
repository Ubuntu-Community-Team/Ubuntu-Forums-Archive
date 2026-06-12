---
title: "&quot;Shutdown&quot; doesn't work"
date: 2006-02-15
forum: General Help
---

### Post by Wermut on 2006-02-15
Hello everybody,

With my Samsung Notebook on Kubuntu Breezy I have a problem I did not encounter with Ubuntu. Shutting down takes either awfully long or sometimes it does not switch the power off at all. It just shows a black screen, but does not really shutdown the notebook.

Can somebody explain this weird behaviour?

---

### Post by Ptero-4 on 2006-02-15
Are the kubuntu and ubuntu you used the same version? I ask b/c the only diference between kubuntu, ubuntu and xubuntu is the desktop GUI being KDE, gnome and xfce respectivelly. The rest of the system components are the same between them as long as you use the same version (e.x: Breezy), but if you're using  Hoary in one and breezy in the other then the compononents are more updated in one and outdated in the other, and that can be the source of your troubles.

---

### Post by Wermut on 2006-02-18
The only version of Ubuntu I have ever installed on this machine is 5.10 (Breezy). I simply thought that it was due to the KDE power management (klaptop).

---

### Post by Wermut on 2006-02-19
What's wrong with this script:
```
#!/bin/sh
# /etc/acpi/powerbtn.sh
# Initiates a shutdown when the power putton has been
# pressed.

[ -f /var/lock/acpisleep ] && exit 0

# If PowerManager is running, let it handle policy
if [ `pidof PowerManager` ]; then
  exit
fi

if ps -Af | grep -q '[k]desktop' && test -f /usr/bin/dcop
then
    dcop --all-sessions --all-users ksmserver ksmserver logout 0 2 0 && exit 0
else
    /sbin/shutdown -h now "Power button pressed"
fi

```

---

