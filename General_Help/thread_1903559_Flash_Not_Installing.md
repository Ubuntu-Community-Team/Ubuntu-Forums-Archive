---
title: "Flash Not Installing"
date: 2012-01-02
forum: General Help
---

### Post by PsyclonJohn on 2012-01-02
Hello,

This problem isn't happening to me, but for a friend I just recently converted to Ubuntu from Windows. However, they aren't able to get Flash to install from the Ubuntu Software Center and have tried other alternatives like flashplugin-nonfree. Whatever the case, she is receiving this message: 

"This error could be caused by required additional software packages which are missing or not installable. Futhermore there could be a conflict between software packages which are not allowed to be installed at the same time."

Does anyone have a solution? She is using 10.04, if it matters.

Thanks,

John

---

### Post by 73ckn797 on 2012-01-02
Did you install ubuntu-restricted-extras? It includes flash as part of the install.

---

### Post by fdrake on 2012-01-02
try
```

sudo apt-get purge flashplugin-nonfree 
sudo apt-get install flashplugin-installer && sudo apt-get update && sudo apt-get upgrade

```

note that :
> 
Package: [COLOR="Red"]flashplugin-nonfree[/COLOR]
State: not installed
Version: 11.1.102.55ubuntu0.10.04.1
Priority: optional
Section: multiverse/web
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 45.1k
[COLOR="Red"]Depends: flashplugin-installer
[/COLOR]
Description: Adobe Flash Player plugin installer (transitional package)
 This package is a transitional package that can safely be removed after you installed flashplugin-installer


---

### Post by syerges on 2012-01-02
she needs to install the flash updater as well so it's current enough to work.

---

### Post by PsyclonJohn on 2012-01-03
Actually, a lot of things aren't installing correctly. I had her try to purge the non-free flash, and it gave back an invalid operation. I don't think the error is from Flash it self, but something going wrong in the OS.

What would cause this? I had her try to fix packages from Synaptic, and it says it fixes, but nothing changes. 

It's a fresh install with only a LAMP web server installed (I intended to teach PHP and MySQLi) but now nothing will install. I've installed many LAMP servers, and this is the first time seeing an experience like this.

Thanks again,

John

---

### Post by claracc on 2012-01-04
Have you tried flash-aid addon for firefox? [https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

It can help to install the correct flash package for your system.

---

### Post by PsyclonJohn on 2012-01-30
Thanks, your Firefox Add-on solution worked like a charm!

Yet, there is still the issue with everything else not installing.

Any one know else know a solution?

---

### Post by sikander3786 on 2012-01-30
> **PsyclonJohn said:**
> Yet, there is still the issue with everything else not installing.

Flash-aid probably succeeded in installing Flash as it downloaded the .tar.gz archive and extracted it, and didn't install the .deb packages.

For the other package related problems, from a Terminal, please post the outputs of these commands:

```
sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a
```

---

### Post by PsyclonJohn on 2012-01-30
Thanks for the reply, 

I've tried that in the past, but realized something last night that is actually pretty strange. It's just Ubuntu Software Center not working correctly. When I install deb's through gdebi it'll work, or when installing packages from Synaptic it'll work, but not from the Ubuntu Software Center.

---

### Post by sikander3786 on 2012-01-31
> **PsyclonJohn said:**
> Thanks for the reply, 

I've tried that in the past, but realized something last night that is actually pretty strange. It's just Ubuntu Software Center not working correctly. When I install deb's through gdebi it'll work, or when installing packages from Synaptic it'll work, but not from the Ubuntu Software Center.
Does the Software Center at least show up? I mean it opens up successfully but only fails in installing the packages?

---

