---
title: "unable to update ubuntu"
date: 2011-08-12
forum: General Help
---

### Post by fuzzylogic25 on 2011-08-12
When i try running the update i get the following messages:

-----------------------------------

W: Failed to fetch [http://dl.google.com/linux/chrome/deb/pool/main/g/google-chrome-stable/google-chrome-stable_13.0.782.107-r94237_i386.deb](http://dl.google.com/linux/chrome/deb/pool/main/g/google-chrome-stable/google-chrome-stable_13.0.782.107-r94237_i386.deb)
  404  Not Found [IP: 74.125.237.15 80]


W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.32-33-generic-pae_2.6.32-33.71_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.32-33-generic-pae_2.6.32-33.71_i386.deb)
  404  Not Found


W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.32-33_2.6.32-33.71_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.32-33_2.6.32-33.71_all.deb)
  404  Not Found


W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.32-33-generic-pae_2.6.32-33.71_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.32-33-generic-pae_2.6.32-33.71_i386.deb)
  404  Not Found


W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.32-33.71_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.32-33.71_i386.deb)
  404  Not Found

--------------------------------------------------------

Is there something wrong on Ubuntus end? Usually update works just fine.

---

### Post by elliotn on 2011-08-12
run
sudo apt-get update

then

sudo apt-get upgrade

---

