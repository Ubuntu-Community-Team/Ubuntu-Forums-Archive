---
title: "Installation Help"
date: 2006-04-30
forum: General Help
---

### Post by Anilkumar on 2006-04-30
I am going to install the new ubuntu now can i have previous archives stored in my computer.How can i load now and install them without referring to net and updating

---

### Post by Ramses de Norre on 2006-04-30
If I understand you correctely, you want to upgrade to dapper and use the archives stored by apt to avoid extra downloading? That wont be possible, all packages are updated for dapper.
If you want to do a fresh breezy install you can copy the .deb's stored in /var/cache/apt/archives over to some save device, do the install, move the .deb's to the new /var/cache/apt/archives and run sudo dpkg -i /var/cache/apt/archives/*

---

### Post by Anilkumar on 2006-05-01
Thank u

---

