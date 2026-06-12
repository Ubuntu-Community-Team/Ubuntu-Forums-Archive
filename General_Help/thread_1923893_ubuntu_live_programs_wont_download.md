---
title: "ubuntu live programs wont download"
date: 2012-02-11
forum: General Help
---

### Post by MrMeen on 2012-02-11
Are u using Live or fully installed? cause i got the same issue with 9.10 live. everything errors out weather its downloaded through terminal or software center

---

### Post by MrMeen on 2012-02-11
This is what im getting

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic universe
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic-updates universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic-updates universe
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic multiverse
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic-updates multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic-updates multiverse
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse

---

### Post by MrMeen on 2012-02-11
When you say "make it look like this" im lost. it looks the same. i tried the second code and it said 
"E: Some index files failed to download, they have been ignored, or old ones used instead."

---

### Post by MrMeen on 2012-02-11
im guessing copying your post and pasting it into the terminal wont work lol. im used to command line, sorry

---

### Post by MrMeen on 2012-02-11
This is what i get when i do the upgrade

```
Ign http://archive.ubuntu.com karmic Release.gpg
Ign http://archive.ubuntu.com karmic/main Translation-en_US
Ign http://archive.ubuntu.com karmic/restricted Translation-en_US
Ign http://security.ubuntu.com karmic-security Release.gpg
Ign http://security.ubuntu.com karmic-security/main Translation-en_US
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US
Ign http://archive.ubuntu.com karmic/universe Translation-en_US
Ign http://archive.ubuntu.com karmic/multiverse Translation-en_US
Ign http://archive.ubuntu.com karmic-updates Release.gpg
Ign http://archive.ubuntu.com karmic-updates/main Translation-en_US
Ign http://archive.ubuntu.com karmic-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com karmic-updates/universe Translation-en_US
Ign http://archive.ubuntu.com karmic-updates/multiverse Translation-en_US
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US
Ign http://archive.ubuntu.com karmic Release   
Ign http://security.ubuntu.com karmic-security Release
Ign http://archive.ubuntu.com karmic-updates Release
Ign http://security.ubuntu.com karmic-security/main Packages
Ign http://archive.ubuntu.com karmic/main Packages
Ign http://archive.ubuntu.com karmic/restricted Packages
Ign http://archive.ubuntu.com karmic/main Sources
Ign http://archive.ubuntu.com karmic/restricted Sources
Ign http://archive.ubuntu.com karmic/universe Packages
Ign http://archive.ubuntu.com karmic/universe Sources
Ign http://archive.ubuntu.com karmic/multiverse Packages
Ign http://security.ubuntu.com karmic-security/restricted Packages
Ign http://security.ubuntu.com karmic-security/main Sources
Ign http://security.ubuntu.com karmic-security/restricted Sources
Ign http://security.ubuntu.com karmic-security/universe Packages
Ign http://security.ubuntu.com karmic-security/universe Sources
Ign http://security.ubuntu.com karmic-security/multiverse Packages
Ign http://archive.ubuntu.com karmic/multiverse Sources
Ign http://archive.ubuntu.com karmic-updates/main Packages
Ign http://security.ubuntu.com karmic-security/multiverse Sources
Ign http://security.ubuntu.com karmic-security/main Packages
Ign http://security.ubuntu.com karmic-security/restricted Packages
Ign http://archive.ubuntu.com karmic-updates/restricted Packages
Ign http://archive.ubuntu.com karmic-updates/main Sources
Ign http://archive.ubuntu.com karmic-updates/restricted Sources
Ign http://archive.ubuntu.com karmic-updates/universe Packages
Ign http://archive.ubuntu.com karmic-updates/universe Sources
Ign http://archive.ubuntu.com karmic-updates/multiverse Packages
Ign http://archive.ubuntu.com karmic-updates/multiverse Sources
Ign http://archive.ubuntu.com karmic/main Packages
Ign http://security.ubuntu.com karmic-security/main Sources
Ign http://security.ubuntu.com karmic-security/restricted Sources
Ign http://security.ubuntu.com karmic-security/universe Packages
Ign http://security.ubuntu.com karmic-security/universe Sources
Ign http://security.ubuntu.com karmic-security/multiverse Packages
Ign http://archive.ubuntu.com karmic/restricted Packages
Ign http://archive.ubuntu.com karmic/main Sources
Ign http://archive.ubuntu.com karmic/restricted Sources
Ign http://archive.ubuntu.com karmic/universe Packages
Ign http://archive.ubuntu.com karmic/universe Sources
Ign http://archive.ubuntu.com karmic/multiverse Packages
Ign http://archive.ubuntu.com karmic/multiverse Sources
Ign http://archive.ubuntu.com karmic-updates/main Packages
Ign http://archive.ubuntu.com karmic-updates/restricted Packages
Ign http://security.ubuntu.com karmic-security/multiverse Sources
Err http://security.ubuntu.com karmic-security/main Packages
  404  Not Found [IP: 91.189.92.166 80]
Ign http://archive.ubuntu.com karmic-updates/main Sources
Ign http://archive.ubuntu.com karmic-updates/restricted Sources
Ign http://archive.ubuntu.com karmic-updates/universe Packages
Ign http://archive.ubuntu.com karmic-updates/universe Sources
Ign http://archive.ubuntu.com karmic-updates/multiverse Packages
Ign http://archive.ubuntu.com karmic-updates/multiverse Sources
Err http://archive.ubuntu.com karmic/main Packages
  404  Not Found [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com karmic/restricted Packages
  404  Not Found [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com karmic/main Sources
  404  Not Found [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com karmic/restricted Sources
  404  Not Found [IP: 91.189.88.31 80]
Err http://security.ubuntu.com karmic-security/restricted Packages
  404  Not Found [IP: 91.189.92.166 80]
Err http://security.ubuntu.com karmic-security/main Sources
  404  Not Found [IP: 91.189.92.166 80]
Err http://security.ubuntu.com karmic-security/restricted Sources
  404  Not Found [IP: 91.189.92.166 80]
Err http://security.ubuntu.com karmic-security/universe Packages
  404  Not Found [IP: 91.189.92.166 80]
Err http://security.ubuntu.com karmic-security/universe Sources
  404  Not Found [IP: 91.189.92.166 80]
Err http://archive.ubuntu.com karmic/universe Packages
  404  Not Found [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com karmic/universe Sources
  404  Not Found [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com karmic/multiverse Packages
  404  Not Found [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com karmic/multiverse Sources
  404  Not Found [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com karmic-updates/main Packages
  404  Not Found [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com karmic-updates/restricted Packages
  404  Not Found [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com karmic-updates/main Sources
  404  Not Found [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com karmic-updates/restricted Sources
  404  Not Found [IP: 91.189.88.31 80]
Err http://security.ubuntu.com karmic-security/multiverse Packages
  404  Not Found [IP: 91.189.92.166 80]
Err http://security.ubuntu.com karmic-security/multiverse Sources
  404  Not Found [IP: 91.189.92.166 80]
Err http://archive.ubuntu.com karmic-updates/universe Packages
  404  Not Found [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com karmic-updates/universe Sources
  404  Not Found [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com karmic-updates/multiverse Packages
  404  Not Found [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com karmic-updates/multiverse Sources
  404  Not Found [IP: 91.189.88.31 80]
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/main/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.166 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/Packages.gz  404  Not Found [IP: 91.189.88.31 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/main/source/Sources.gz  404  Not Found [IP: 91.189.92.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/source/Sources.gz  404  Not Found [IP: 91.189.92.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/source/Sources.gz  404  Not Found [IP: 91.189.92.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.166 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/binary-i386/Packages.gz  404  Not Found [IP: 91.189.88.31 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/main/source/Sources.gz  404  Not Found [IP: 91.189.88.31 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/source/Sources.gz  404  Not Found [IP: 91.189.88.31 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.gz  404  Not Found [IP: 91.189.88.31 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/universe/source/Sources.gz  404  Not Found [IP: 91.189.88.31 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-i386/Packages.gz  404  Not Found [IP: 91.189.88.31 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/multiverse/source/Sources.gz  404  Not Found [IP: 91.189.88.31 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-i386/Packages.gz  404  Not Found [IP: 91.189.88.31 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/binary-i386/Packages.gz  404  Not Found [IP: 91.189.88.31 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/source/Sources.gz  404  Not Found [IP: 91.189.92.166 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/source/Sources.gz  404  Not Found [IP: 91.189.88.31 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/source/Sources.gz  404  Not Found [IP: 91.189.88.31 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-i386/Packages.gz  404  Not Found [IP: 91.189.88.31 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/source/Sources.gz  404  Not Found [IP: 91.189.88.31 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-i386/Packages.gz  404  Not Found [IP: 91.189.88.31 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/source/Sources.gz  404  Not Found [IP: 91.189.88.31 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.
ubuntu@ubuntu:~$ 

```


Would the fact that im using a live usb be the problem. if so how do i get around it. thanks for the help so far

---

### Post by MrMeen on 2012-02-11
Im not sure i understand where im supposed to put the #. I apologize.

---

### Post by MrMeen on 2012-02-11
Not able to download or install programs on ubuntu live 9.10. im running it off a usb stick if that helps at all.

---

### Post by jerrrys on 2012-02-11
EOL

[http://fridge.ubuntu.com/2011/05/26/ubuntu-9-10-karmic-koala-end-of-life-reached-on-april-30-2011/](http://fridge.ubuntu.com/2011/05/26/ubuntu-9-10-karmic-koala-end-of-life-reached-on-april-30-2011/)

---

### Post by oldos2er on 2012-02-12
Threads merged. 

As jerrrys says, 9.10 is End of Life, and its repositories are offline. You will need to use version 10.04 or newer.

---

