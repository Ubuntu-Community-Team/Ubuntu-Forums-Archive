---
title: "Running Firefox off of /media"
date: 2011-06-19
forum: General Help
---

### Post by Curse on 2011-06-19
My gf's laptop hasn't been booting up, I have another thread up about that. It is running Linux Mint 10 64bit. If I attach her HDD to my Desktop, or use a live CD (thumb drive), I can access the HDD as a mounted device. The folders work fine, I've backed up most of the important info if we do need to reformat. 

One thing I need is her Bookmarks and Passwords from Firefox. I had the idea of running Firefox from the mounted disk, but I can't seem to get FF to load with the settings and information from the install on the HDD.

Can anyone tell me what folder I need to go to to either get this information or to get FF to load with the pertainant info? I've been trying:

```

/media/HDD/usr/lib/firefox-3*/firefox

```

and 

```

/media/HDD/usr/lib64/firefox-3*/firefox

```

Ideas?

---

### Post by bodhi.zazen on 2011-06-19
The data you need is in the old home direcroty, in .mozilla/firefox, under the profile name.

See this link for passwords:

[http://blog.bodhizazen.net/linux/transfer-firefox-4-passwords/](http://blog.bodhizazen.net/linux/transfer-firefox-4-passwords/)

bookmarks are in bookmarks.html

---

### Post by Curse on 2011-06-20
> **bodhi.zazen said:**
> The data you need is in the old home direcroty, in .mozilla/firefox, under the profile name.

See this link for passwords:

[http://blog.bodhizazen.net/linux/transfer-firefox-4-passwords/](http://blog.bodhizazen.net/linux/transfer-firefox-4-passwords/)

bookmarks are in bookmarks.html

Thank ya :D

---

