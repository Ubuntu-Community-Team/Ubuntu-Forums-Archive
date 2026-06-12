---
title: "404s for apt-get"
date: 2011-01-14
forum: General Help
---

### Post by jupo on 2011-01-14
Trying to install the libssl-dev package and I receive the following output indicating 404 errors. Indeed taking a look at the directory referenced in the URLs shows that the server is perfectly accessible yet the particular versions of the files don't exist. I don't know much about packaging, any idea how to get the package I need installed? Thanks.


The following extra packages will be installed:
  libssl0.9.8
The following NEW packages will be installed:
  libssl-dev
The following packages will be upgraded:
  libssl0.9.8
1 upgraded, 1 newly installed, 0 to remove and 112 not upgraded.
Need to get 4773kB of archives.
After this operation, 5665kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main libssl0.9.8 0.9.8g-4ubuntu3.9
  404 Not Found [IP: 91.189.88.40 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main libssl0.9.8 0.9.8g-4ubuntu3.9
  404 Not Found [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main libssl-dev 0.9.8g-4ubuntu3.9
  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8g-4ubuntu3.9_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8g-4ubuntu3.9_i386.deb)  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl-dev_0.9.8g-4ubuntu3.9_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl-dev_0.9.8g-4ubuntu3.9_i386.deb)  404 Not Found [IP: 91.189.92.167 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by Smart Viking on 2011-01-14
```
sudo apt-get update && sudo apt-get update --fix-missing
```

If you can't get it installed after that, download the .deb you want and install it with 
```
sudo dpkg -i something.deb
```

---

### Post by papibe on 2011-01-14
I hate when that happens! Unfortunately servers are down once in a while. If the installation is not urgent, just wait a few hours or until tomorrow.

If it is, you can change the download server for one that is up, and closer to you (in terms of response time). Check the section "Download Server" on this [page]("https://help.ubuntu.com/community/Repositories/Ubuntu") (Other -> Best Server). 

It takes a while to determine which one is the better (a few minutes), but it's totally worth it.

Good Luck!

---

### Post by jupo on 2011-01-14
I just tried the ones in the same directory that looked like the closest match and using your manual approach worked perfectly. Thanks for your help.

---

