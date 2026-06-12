---
title: "Downgrading packet (libc6)"
date: 2010-02-17
forum: General Help
---

### Post by genius_mkd on 2010-02-17
I installed wrong version from this package (I didn't knew that libc6 was very important package) so now i get a lot of errors. I tracked the original version and downloaded it. I have it on my PC as .deb package but i can't install it because it's older version then the installed one. 
Normally, I would first remove the old package and then install new. But now I'm not sure because I don't know will my edubuntu work without the libc6 package.
P.S. Version of my edbuntu is 7.04 installed on asus eee 900HA. I only have internet on my desktop PC.

---

### Post by zvacet on 2010-02-18
If you just uninstall new version you should be able to install it again because it should be in /var/cache/apt/archives.Even better solution is to back up all your important data/files and install supported version of Ubuntu.You can take latest (Karmic).

---

### Post by gmargo on 2010-02-18
> **genius_mkd said:**
> I have it on my PC as .deb package but i can't install it because it's older version then the installed one. 
Normally, I would first remove the old package and then install new. 

How did you try to install it?  You are correct in that you cannot uninstall an essential package first. You'll probably have to use "**dpkg -i filename.deb**", with perhaps a sprinkling of **--force** options.  See the **dpkg** man page for full info.

But backup anything critical first because you could easily end up with an unbootable system.

---

