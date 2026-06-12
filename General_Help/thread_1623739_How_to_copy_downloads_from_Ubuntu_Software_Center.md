---
title: "How to copy downloads from Ubuntu Software Center"
date: 2010-11-17
forum: General Help
---

### Post by ram2500 on 2010-11-17
Hello and long time, no see!

I would like to know where Ubuntu Software Center downloads the packages until they are installed. The reason I ask is because I would like to snag the packages that are being downloaded and back them up, so if I do a reinstall, I don't have to wait for the packages to download. I've tried aptonacd with no success *multiple times*, and so I thought that perhaps I could just create a backup CD with the .deb files of the packages I download in the future. I am planning to do a reinstall soon to make more room for Ubuntu, so I would like to get the packages as they are downloaded copied for backup. 

Any ideas greatly appreciated!
-ram2500

---

### Post by bryangwilliam on 2010-11-17
Packages are downloaded to /var/cache/apt/archives

If you want to just download without installing the packages, add a -d to your apt-get command

---

### Post by ram2500 on 2010-11-17
Thanks a lot! This will be really helpful as it will be less of a headache to spend an hour or two downloading my frequently used programs after a reinstall.

---

