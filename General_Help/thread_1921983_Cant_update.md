---
title: "Cant update"
date: 2012-02-07
forum: General Help
---

### Post by searayman on 2012-02-07
Trying to update my system and am getting this:

[IMG]http://imageshack.us/photo/my-images/803/screenshotat20120207200.png/[/IMG]

error is:


Failed to fetch [http://ppa.launchpad.net/me-davidsansome/clementine-dev/ubuntu/pool/main/c/clementine/clementine_1.0.1-154-gb86be65~oneiric_i386.deb](http://ppa.launchpad.net/me-davidsansome/clementine-dev/ubuntu/pool/main/c/clementine/clementine_1.0.1-154-gb86be65~oneiric_i386.deb) 404  Not Found
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/e/evince/evince_3.2.1-0ubuntu2.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/e/evince/evince_3.2.1-0ubuntu2.1_i386.deb) 404  Not Found [IP: 91.189.92.182 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/e/evince/libevince3-3_3.2.1-0ubuntu2.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/e/evince/libevince3-3_3.2.1-0ubuntu2.1_i386.deb) 404  Not Found [IP: 91.189.92.182 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/e/evince/evince-common_3.2.1-0ubuntu2.1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/e/evince/evince-common_3.2.1-0ubuntu2.1_all.deb) 404  Not Found [IP: 91.189.92.182 80]

---

### Post by jonobr on 2012-02-07
Hey


What happens when you open a terminal and 

```
ping us.archive.ubuntu.com
```

does it work?

What happens when you do

```
sudo apt-get update
```

post the errors from that and lets see 

If that does somethine then
```
sudo apt-get upgrade
```

---

