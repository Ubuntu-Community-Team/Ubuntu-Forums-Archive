---
title: "Firefox plugin error"
date: 2011-03-29
forum: General Help
---

### Post by saguran on 2011-03-29
Hi,

I'm quite new to Linux, so forgive me if this is silly.  Firefox needed some additional plugins to display things like flash player and gnash.  After the one installation, the installation froza and I had to restart.  

Now when I go into the Synaptic Package Manager it just says that it has encountered an error and that I have to manually run 'sudo dpkg -- configure -a'.

When I run this it says that configure needs an action. I've tried the help but still no avail.

Any help would be appreciated.

Thanks.

Francois

---

### Post by garvinrick4 on 2011-03-29
Either go to Synaptics and uninstall flashplugin-installer
and then install.
or open a terminal and:
```
sudo apt-get purge flashplugin-installer
``````
sudo apt-get install flashplugin-installer
```Package: flashplugin-installer           
State: installed
Automatically installed: no
Version: 10.2.153.1ubuntu1
Priority: optional
Section: multiverse/web
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>

---

### Post by saguran on 2011-03-29
Thanks garvinrick4, I've resolved the problem.

Francois

---

