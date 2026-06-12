---
title: "Unable to update"
date: 2010-05-20
forum: General Help
---

### Post by akssps011 on 2010-05-20
Hi

I am using kubuntu 9.04.
When I try to update (bug fixes and security patches) through KPackage Kit, it shows the following error:

 p, li { white-space: pre-wrap; }  The package download failed.
 Please check your network connectivity.
The Details section shows this


```


p, li { white-space: pre-wrap; } Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.31-21-generic_2.6.31-21.59_i386.deb Could not connect to in.archive.ubuntu.com:80 (111.91.91.37), connection timed out
Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/main/b/boost1.38/libboost-program-options1.38.0_1.38.0-6ubuntu6.1_i386.deb Unable to connect to in.archive.ubuntu.com http:
Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-generic_2.6.31.21.34_i386.deb Unable to connect to in.archive.ubuntu.com http:
Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_2.6.31.21.34_i386.deb Unable to connect to in.archive.ubuntu.com http:
Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.31-21_2.6.31-21.59_all.deb Unable to connect to in.archive.ubuntu.com http:
Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.31-21-generic_2.6.31-21.59_i386.deb Unable to connect to in.archive.ubuntu.com http:
Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_2.6.31.21.34_i386.deb Unable to connect to in.archive.ubuntu.com http:



```


Even if I try to install anything via KPackageKit it shows the same error.

Is it a problem with ubuntu repository ? What should I do ?

---

### Post by ankit.vader on 2010-05-20
go to update manager-> settings. Under 'Ubuntu Software' tab change the server to main server.

---

