---
title: "changing bittornado d/l directory"
date: 2010-10-11
forum: General Help
---

### Post by Jethro_uk on 2010-10-11
Hi all

installed torrentflux and set it up no problem. Can log in and add torrents. However, trying to start torrents doesn't work.

I tried to change the d/l directory using torrentflux, to an external USB drive, where the d/l dir is owned by root.

If I change the d/l directory to /usr/share/torrentflux/www/downloads, then the downloads run fine.

I suspect this is a bittornado problem with file/directory permissions.

I tried chmod 777 -R /mydownloaddir, but that hasn't worked.

Can anyone please suggest what directory permissions are needed for bittornado to work ?

If it helps the actual directory structure of where I want the downloads to go is :

/dir1/dir2/dir3/files

thanks guys

---

### Post by Jethro_uk on 2010-10-12
Looking in the Apache2 logs, it seems BitTornado does not like spaces in the path for the download directory

so I changed \Media Files to \Media_Files and hey presto !!!!!

It worked.

---

