---
title: "Ubuntu Repo problems"
date: 2010-10-19
forum: General Help
---

### Post by yusuo85 on 2010-10-19
After updating to maverick im having trouble updating basically everytime I go to check my for updates i get confronted with this error
"W:Failed to fetch [http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead."

I dont know why this is going on and how i can fix it 

Heres a copy of my sources

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb [http://archive.canonical.com/](http://archive.canonical.com/) maverick partner
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) maverick main # disabled on upgrade to maverick
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main #Third party developers repository



If anyone can point me in how the hell i fix this it would be appreciated

---

### Post by Lazaruss on 2010-10-19
well, there is no maverick folder in [http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu/dists/](http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu/dists/), which gives the 404 error, you're requesting a ppa that doesn't exist. Is that all of your sources list?

---

### Post by yusuo85 on 2010-10-19
yes according to sources.lst thats all of my repo's

is there anyway someone can give me a list of there official repos so i can just start from what im supposed to have, this is apgrade from lucid

---

### Post by coffeecat on 2010-10-19
> **yusuo85 said:**
> yes according to sources.lst thats all of my repo's

PPA and 3rd party repositories usually go in their own *.list files in /etc/apt/sources.list.d/ . Have a look there for the source causing the problem.

> **yusuo85 said:**
> is there anyway someone can give me a list of there official repos so i can just start from what im supposed to have, this is apgrade from lucid

You can generate a fresh sources.list here:

[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

