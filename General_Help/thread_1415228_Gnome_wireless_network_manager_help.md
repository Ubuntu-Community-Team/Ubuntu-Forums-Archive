---
title: "Gnome wireless network manager help"
date: 2010-02-24
forum: General Help
---

### Post by Havek on 2010-02-24
The other day I removed all the bluetooth packages on my laptop since I don't ever use them.  Upon restart the gnome wireless manager on my panel disappeared leaving me no way to connect to wireless networks.  I tried reinstalling the packages I removed but this did nothing.  Does anyone know how to fix this, or the name of the package for the gnome network manager. Thanks.

---

### Post by mac9416 on 2010-02-24
Hey, Havok,

Is the package 'network-manager-gnome'?

Tip: you can search for packages from the command line with 'apt-cache search <package>'. That's how I found that package name.  :)

Hope that helps!

---

### Post by spiderbatdad on 2010-02-24
Also to see which packages you have installed:
```
dpkg --list
```
Not sure how you removed the installed packages, but in this situation it is usually more desirable to just disable the service rather than risk removing packages the system needs. For example:
```
update-rc.d -f bluetooth remove
## to stop the running service after the above command without having to reboot ##
/etc/init.d/bluetooth stop

```

---

### Post by Havek on 2010-02-24
> **mac9416 said:**
> Hey, Havok,

Is the package 'network-manager-gnome'?

Tip: you can search for packages from the command line with 'apt-cache search <package>'. That's how I found that package name.  :)

Hope that helps!

Yup that was it, I must have been searching for gnome-network instead of network-manager-gnome.

Thanks for the help

---

