---
title: "Install packages to /opt/&lt;Some_Name&gt;/ folder?"
date: 2009-10-18
forum: General Help
---

### Post by nerdopolis on 2009-10-18
Is it possible to force apt or dpkg to install to a folder in the /opt/<Some_Name> folder? I know some packages like the ones from KDE neon will install to /opt/kde-neon, but that seems to be hard coded in the package files themselves.

I'm going to have /opt as a mount point for removable media, so that I can temproraly have them acessible by a system without perminantly installing them.

---

### Post by nikhilbhardwaj on 2009-10-18
not likely
the .deb files have a particular installation target
generally /usr
but you can comipile an install packages yourself
and install them to any location

---

### Post by nerdopolis on 2009-10-18
I was afraid of that.

Thanks for the reply though. I'll have to try a union mount with aufs, so programs and data can be read from /usr, but writes get redirected to /opt/<Some_Name> when apt is running.

If that doesn't work, *then* I'll resort to compiling.

---

