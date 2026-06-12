---
title: "vdr error reading channels.conf"
date: 2006-01-30
forum: General Help
---

### Post by philipgm on 2006-01-30
Has anyone seen a HOW TO to set up vdr? 

I've installed from the repositories and downloaded and compiled and I still get the message:

error reading channels.conf

The file exists and is owned by the vdr user. There is no problem with file permissions (since I did CHMOD 777).

Any help, advice, thoughts would be appreciated.

hanks

Phil

---

### Post by philipgm on 2006-01-30
Never mind. It turns out that there's an error in the channels.conf file on the CH14 line.

I opened it as a CSV in OO and it stood out like a sore thumb! I deleted that line and that problem has gone away. Now to get the rest of it working... Onwards and upwards.

---

