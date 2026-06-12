---
title: "Repos"
date: 2012-05-13
forum: General Help
---

### Post by kswitch on 2012-05-13
Pls i need help


anytime i run 

sudo apt-get update

dis is what i get at the ending of the whole fetching


W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease: File /var/lib/apt/lists/partial/extras.ubuntu.com_ubuntu_dists_oneiric_InRelease doesn't start with a clearsigned message
W: GPG error: [http://dl.google.com](http://dl.google.com) stable InRelease: File /var/lib/apt/lists/partial/dl.google.com_linux_earth_deb_dists_stable_InRelease doesn't start with a clearsigned message
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease: File /var/lib/apt/lists/partial/archive.canonical.com_ubuntu_dists_oneiric_InRelease doesn't start with a clearsigned message
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric InRelease: File /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric_InRelease doesn't start with a clearsigned message
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates InRelease: File /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-updates_InRelease doesn't start with a clearsigned message
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports InRelease: File /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-backports_InRelease doesn't start with a clearsigned message
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security InRelease: File /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-security_InRelease doesn't start with a clearsigned message
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/main/i18n/Index](http://extras.ubuntu.com/ubuntu/dists/oneiric/main/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/extras.ubuntu.com_ubuntu_dists_oneiric_main_i18n_Index

W: Failed to fetch [http://dl.google.com/linux/earth/deb/dists/stable/main/i18n/Index](http://dl.google.com/linux/earth/deb/dists/stable/main/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/dl.google.com_linux_earth_deb_dists_stable_main_i18n_Index

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/oneiric/partner/i18n/Index](http://archive.canonical.com/ubuntu/dists/oneiric/partner/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/archive.canonical.com_ubuntu_dists_oneiric_partner_i18n_Index

E: Some index files failed to download. They have been ignored, or old ones used instead.


i figure it is coming from the google earth i installled bt i am also seeing d canonical link there so i dont want to do anything that will crash by OS

pls i need help....

---

### Post by Frogs Hair on 2012-05-13
It appears as if unsupported updates and back-ports may be enabled. If so this can can cause problems like you are seeing. Another result of this is partial upgrades and broken packages. If this is the case you may have to wait until the packages are available.

---

### Post by howefield on 2012-05-13
Posts moved to own thread.

---

