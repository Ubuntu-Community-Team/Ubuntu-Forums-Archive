---
title: "&quot;Could not download all required packages&quot; while installing .deb files."
date: 2009-12-09
forum: General Help
---

### Post by RJ12 on 2009-12-09
Ok we got a problem here it says "Could not download all required packages" but I can connect to the internet fine. I'm gonna take a guess that it has something to do with PPAs? I have no clue.

By the way I'm trying to use the Google Chrome .deb file from Google (Yes they just released a offical Linux build in .deb and .rpm (Fedora/openSuse)

Please help

Edit: The title said/says file**s** it only happens on this Google Chrome one and VirtualBox (I got VMware Player 3) so it dosent matter

Update Again: Here is the exact message under details: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/n/nss/libnss3-1d_3.12.3.1-0ubuntu0.9.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/n/nss/libnss3-1d_3.12.3.1-0ubuntu0.9.04.1_i386.deb) 404 Not Found

---

### Post by RJ12 on 2009-12-09
okay I found this package libnss3-1d_3.12.3.1-0ubuntu0.9.04.2_i386.deb by taking off the filename and looking through the list of files. I found the difference is the 2_i386.deb when google chrome wants 1_i386.deb If I download and install the 2_ file will it work

---

### Post by RJ12 on 2009-12-09
Solved, Installed Chromium

---

