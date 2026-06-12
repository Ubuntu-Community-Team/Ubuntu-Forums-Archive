---
title: "Package Manager Install Directory"
date: 2010-01-30
forum: General Help
---

### Post by Scooter_X on 2010-01-30
How in the blazes do I change the installation directory in Synaptic? I've got a small partition for Ubuntu and a large partition that is for sharing everything between Ubuntu and Windows 7 (dual boot) and I'd like to keep from using space on my ubuntu partition if I can... Any help greatly appreciated. Thanks!

---

### Post by todak on 2010-01-30
Synaptic does not decide where to install packages, the package writer and the system determine that. The actual .deb files are stored in /var/cache/apt on the ubuntu drive. If you do not want the main ubuntu partition to fill because of the cache size, you can empty the cache through synaptic after installing the packages or you can create a separate partition for /var. As far as the actual installed programs, they are installed (usually) in /usr/bin. It will grow with the number of installed programs on the ubuntu drive, there is no way to avoid the growth. Again, creating a separate partition is the only way to go. But then /usr/share/doc usr/share/blah,blah will also grow, along with any data created in your /home/<your-user-name-here>. Unless you want to create a separate partition for every folder, you cannot avoid your ubuntu partition getting filled.

---

### Post by Scooter_X on 2010-01-30
Dang. Well, thanks for the info.

---

