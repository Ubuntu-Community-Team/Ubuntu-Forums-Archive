---
title: "How to force install a package without dependencies"
date: 2006-02-08
forum: General Help
---

### Post by jcl on 2006-02-08
Howdy,

I'm wanting to install 'squid-cgi' through either apt-get, aptitude or synaptic and it pulls in 'webmin' and 'webmin-squid' as dependencies. The problem is since the version of webmin in the repository is broken I've had to install webmin manually. If I allow the install to proceed with the webmin packages, it will break my existing, working webmin install.

So, how do I force one of these three installation methods to install 'squid-cgi' *only*?

For apt-get, I see no flags in the man page that would indicate this type of action.

For aptitude, I *can* deselect packages to be installed with the '-' key, *but* after doing so it marks 'squid-cgi' as broken and will not install it.

For synaptic, I see no way to deselect dependencies.

Help!!! I don't want to manually install 'squid-cgi' too because I love the pacakage management tools and I don't want yet more 'unregistered' software on the system to have to maintain manually (which could be a dependency of some other software, if that makes sense). I would even uninstall webmin and install from the repository if the version out there worked!!!! Help!

Thanks!

---

### Post by MartinG on 2006-02-08
To avoid the problem of unregistered software, install and use checkinstall.  You run configure and make as normal, but for the last stage you run "sudo checkinstall" instead of "sudo make install".  This then generates a deb file and installs it with dpkg, so it is registered (it shows up in synaptic under "local or obsolete").

This may be too late for your present problem, but if you're willing to uninstall webmin you could re-install it using checkinstall, and that should cover it -- I hope :)

---

### Post by kaamos on 2006-02-08
You can also download the package from packages.ubuntu.com and use change the package dependencies. Howto -> [https://wiki.ubuntu.com/SkypeHowto#head-2fab847bad2d0fbcf939828c5c7ec3dc7af99a1b](https://wiki.ubuntu.com/SkypeHowto#head-2fab847bad2d0fbcf939828c5c7ec3dc7af99a1b)

---

### Post by jcl on 2006-02-08
Awesome... that worked! I've now installed it and locked the version in synaptic so it won't be tempted to update it.

Thanks

---

