---
title: "Virtual Machine Unable to Update"
date: 2012-09-19
forum: General Help
---

### Post by cfree220 on 2012-09-19
Hi,

I am running 12.04 in virtualbox 4.1.8.

When I try to download and install updates, I get the error that it "Failed to Download package files" and that I should check my internet connection. Internet is working (I am posting this from the virtual machine).

The details output is as follows:


```
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/b/bind9/bind9-host_9.8.1.dfsg.P1-4ubuntu0.2_i386.deb 404  Not Found [IP: 91.189.92.190 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/b/bind9/dnsutils_9.8.1.dfsg.P1-4ubuntu0.2_i386.deb 404  Not Found [IP: 91.189.92.190 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/b/bind9/libisc83_9.8.1.dfsg.P1-4ubuntu0.2_i386.deb 404  Not Found [IP: 91.189.92.190 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/b/bind9/libdns81_9.8.1.dfsg.P1-4ubuntu0.2_i386.deb 404  Not Found [IP: 91.189.92.190 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/b/bind9/libisccc80_9.8.1.dfsg.P1-4ubuntu0.2_i386.deb 404  Not Found [IP: 91.189.92.190 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/b/bind9/libisccfg82_9.8.1.dfsg.P1-4ubuntu0.2_i386.deb 404  Not Found [IP: 91.189.92.190 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/b/bind9/liblwres80_9.8.1.dfsg.P1-4ubuntu0.2_i386.deb 404  Not Found [IP: 91.189.92.190 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/b/bind9/libbind9-80_9.8.1.dfsg.P1-4ubuntu0.2_i386.deb 404  Not Found [IP: 91.189.92.190 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/eog/eog_3.4.2-0ubuntu1_i386.deb 404  Not Found [IP: 91.189.91.24 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-globalmenu_15.0+build1-0ubuntu0.12.04.1_i386.deb 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_15.0+build1-0ubuntu0.12.04.1_i386.deb 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-gnome-support_15.0+build1-0ubuntu0.12.04.1_i386.deb 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-en_15.0+build1-0ubuntu0.12.04.1_i386.deb 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-input-synaptics/xserver-xorg-input-synaptics_1.6.2-1ubuntu1~precise1_i386.deb 404  Not Found [IP: 91.189.91.24 80]
```

Any thoughts on this?

---

### Post by jerrrys on 2012-09-20
Have you tried changing your software source?

[https://help.ubuntu.com/community/Repositories/Ubuntu#Download_Server](https://help.ubuntu.com/community/Repositories/Ubuntu#Download_Server)

---

### Post by dcstar on 2012-09-20
> **cfree220 said:**
> Hi,

I am running 12.04 in virtualbox 4.1.8.

When I try to download and install updates, I get the error that it "Failed to Download package files" and that I should check my internet connection. Internet is working (I am posting this from the virtual machine).

The details output is as follows:
........

The Repository package list was updated before the actual packages were available in a repository.

Wait a day or so and it will be resolved.

---

