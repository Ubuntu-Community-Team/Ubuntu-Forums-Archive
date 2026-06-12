---
title: "what sources should I be using?"
date: 2004-10-21
forum: General Help
---

### Post by Vulc on 2004-10-21
hiya, when I was trying to install my radeon card I get a package not found error for fglrx-driver, I haven't deleted any of my sources I don't think so what new ones should I enter? I really want to install my card but this lack of correct sources is a pain =(

---

### Post by Rancoras on 2004-10-21
Give us a look at your sources.list

---

### Post by Vulc on 2004-10-21
## Uncomment the following two lines to fetch updated software from the network


## Uncomment the following two lines to add software from the 'universe'
#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty universe
deb [http://ftp.tux.org/pub/java/debian](http://ftp.tux.org/pub/java/debian) woody non-free
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) warty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) warty-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty multiverse

#deb [http://http.us.debian.org/debian](http://http.us.debian.org/debian) stable main contrib non-free
#deb [http://non-us.debian.org/debian-non-US](http://non-us.debian.org/debian-non-US) stable/non-US main contrib non-free

#deb [http://http.us.debian.org/debian](http://http.us.debian.org/debian) unstable main contrib non-free
#deb [http://non-us.debian.org/debian-non-US](http://non-us.debian.org/debian-non-US) unstable/non-US main contrib non-free

#deb [http://http.us.debian.org/debian](http://http.us.debian.org/debian) testing main contrib non-free
#deb [http://non-us.debian.org/debian-non-US](http://non-us.debian.org/debian-non-US) testing/non-US main contrib non-free
e
#deb [http://non-us.debian.org/debian-non-US](http://non-us.debian.org/debian-non-US) stable/non-US main contrib non-free

deb [http://http.us.debian.org/debian](http://http.us.debian.org/debian) unstable main contrib non-free
deb [http://non-us.debian.org/debian-non-US](http://non-us.debian.org/debian-non-US) unstable/non-US main contrib non-free

#deb [http://http.us.debian.org/debian](http://http.us.debian.org/debian) testing main contrib non-free
#deb [http://non-us.debian.org/debian-non-US](http://non-us.debian.org/debian-non-US) testing/non-US main contrib non-free

---

### Post by Vulc on 2004-10-21
k nm, I'm retarded, lines are still commented, thanks lol!

---

### Post by Rancoras on 2004-10-21
It's also not a good idea to mix debian and ubuntu sources.

[http://www.ubuntulinux.org/support/documentation/faq/helpcenterfaq.2004-09-15.7453904394](http://www.ubuntulinux.org/support/documentation/faq/helpcenterfaq.2004-09-15.7453904394)

---

### Post by HungSquirrel on 2004-10-21
I added a Debian source to my sources.list and I leave it commented out.  When I need a package that isn't in universe I uncomment it, update, install, and then comment it back.  I only do this for packages with no dependencies or for which I already have the dependencies.  It's not recommended, but it has worked for me so far.

---

