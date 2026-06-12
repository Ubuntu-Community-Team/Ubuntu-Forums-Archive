---
title: "Corrupt deb packages - How to Remove?"
date: 2009-07-09
forum: General Help
---

### Post by PlatosGimp on 2009-07-09
I have been having nothing but trouble getting flash and jscript running in FF 3.5 under Ubuntu 9.04. The stage I am at now is an attempted install of the flashplugin-installer got interupted due to a crash and so now I can install or uninstall anything.

When I try to force removal I get this:

jstork@johnny-lt:/var/cache/apt/archives$ sudo dpkg --force-all -i flashplugin-installer_10.0.22.87ubuntu2_i386.deb 
(Reading database ... 168026 files and directories currently installed.)
Preparing to replace flashplugin-installer 10.0.22.87ubuntu2 (using flashplugin-installer_10.0.22.87ubuntu2_i386.deb) ...
dpkg (subprocess): unable to execute old pre-removal script: Exec format error
dpkg: warning - old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
prerm called with unknown argument `failed-upgrade'
dpkg: error processing flashplugin-installer_10.0.22.87ubuntu2_i386.deb (--install):
 subprocess new pre-removal script returned error exit status 1
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 flashplugin-installer_10.0.22.87ubuntu2_i386.deb


## Elsewhere I found a post that suggested to run this below, but still no luck.

jstork@johnny-lt:/var/cache/apt/archives$ sudo dpkg --configure -a
dpkg: error processing flashplugin-installer (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 flashplugin-installer

Desperately Seeking Help...Anyone have any ideas?

---

### Post by synapsys on 2009-07-09
> **PlatosGimp said:**
> 
When I try to force removal I get this:

jstork@johnny-lt:/var/cache/apt/archives$ sudo dpkg --force-all -i flashplugin-installer_10.0.22.87ubuntu2_i386.deb 


-i___means install
-r___means remove

Might be a typo here, just double checking.

---

### Post by jdkchem on 2009-07-23
Same problem 

```
sudo dpkg --force-all -r python-skype
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.

```

If I try to reinstall I told the archive does not exist.

Cannot reinstall + cannot remove = STUPID

---

### Post by Strongman332 on 2009-07-23
try using the broken filter in synaptic

---

### Post by Zorael on 2009-07-23
Use **aptitude reinstall** to reinstall stuff, instead of just replacing existing, which is what dpkg -i does as far as I'm aware.

---

