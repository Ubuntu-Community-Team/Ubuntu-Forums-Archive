---
title: "Login session error. Only fail safe login works"
date: 2009-11-28
forum: General Help
---

### Post by phenest on 2009-11-28
When I login to Gnome, I get an error stating there is either an installation problem or I'm out of disk space (more than 80GB left). I'm able to login to a Gnome fail safe session though.

I think the problem may be my fault as I was deleting some old config files from the /home folder for apps that have been removed.

This is the contents of the .xsession-errors file:
```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_GB.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/usr/bin/ssh-agent: error while loading shared libraries: libgssapi_krb5.so.2: cannot open shared object file: No such file or directory
```

---

### Post by phenest on 2009-11-28
I've narrowed this down to a package called libgssapi-krb5-2 in Karmic. I'm running Jaunty, but this is due to my own carelessness. I changed the sources list using:
```
sudo sed -i 's/jaunty/karmic/g' /etc/apt/sources.list
```
...so I could upgrade virtualbox-ose to Karmic's version. Then I decided to remove virtualbox-ose as I changed my mind.

I've used Synaptic to remove any residual config files, but to no avail.

---

### Post by phenest on 2009-11-28
A solution is to comment out 'use-ssh-agent' from /etc/X11/Xsession.options. But is that safe?

---

### Post by phenest on 2009-11-28
> **phenest said:**
> A solution is to comment out 'use-ssh-agent' from /etc/X11/Xsession.options. But is that safe?

Nope. Not a good idea. Many Gnome apps won't start. Only solution was to download the libgssapi-krb5-2 package and install it.

This is only a workaround seeing as this package shouldn't be on my system. I'd sooner have a better solution so as to not need this package.

Ideas?

---

