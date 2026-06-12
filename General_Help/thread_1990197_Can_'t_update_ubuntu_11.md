---
title: "Can 't update ubuntu 11"
date: 2012-05-29
forum: General Help
---

### Post by MrStranger on 2012-05-29
When i use update command : sudo apt-get update  i get this .... 


Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en   
Get:75 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en [1,954 B]
Fetched 19.3 MB in 32s (595 kB/s)                                              
W: Failed to fetch [http://ppa.launchpad.net/marko-techytalk.info/ralink-wireless/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/marko-techytalk.info/ralink-wireless/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/marko-techytalk.info/ralink-wireless/ubuntu/dists/precise/main/binary-amd64/Packages](http://ppa.launchpad.net/marko-techytalk.info/ralink-wireless/ubuntu/dists/precise/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/marko-techytalk.info/ralink-wireless/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/marko-techytalk.info/ralink-wireless/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.


Thanks for ur help

---

### Post by dino99 on 2012-05-29
no need to worry about the first lines (translation) you will often see such warnings

about the ppa url, check with your browser that they are still alive for your distro (lot of them dont have the "sources" entry, so delete these lines

---

### Post by MrStranger on 2012-05-29
Thanks i will try this

---

### Post by 2F4U on 2012-05-29
The url's in the error message are not accessible, at least not at the moment. So, either this is a temporary problem or the ppa is gone.

---

