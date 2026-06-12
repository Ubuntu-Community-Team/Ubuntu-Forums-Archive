---
title: "R installation problem"
date: 2009-06-28
forum: General Help
---

### Post by Tiganjero on 2009-06-28
I'm an archeology student and the program R ([link]("http://www.r-project.org/")) is really important to me. I tried to install it, but no luck. Please help me, it's very important. :)

---

### Post by mikewhatever on 2009-06-28
What was the problem? The program is in the repositories, and can be installed with **sudo apt-get install r-base**.

---

### Post by Tiganjero on 2009-06-28
Never mind, :D

---

### Post by Philotus on 2009-09-13
If you still want to install R, an excellent decision by the way, get the current repositories from the R site and use synaptic to install r-base.

[http://cran.r-project.org/bin/linux/ubuntu/]("http://cran.r-project.org/bin/linux/ubuntu/")

Note that the repositories on this page must be completed with a mirror from the R website.

Ex:
deb http://<my.favorite.cran.mirror>/bin/linux/ubuntu jaunty/
becomes the following for Germany:
deb [http://mirrors.softliste.de/cran/bin/linux/ubuntu](http://mirrors.softliste.de/cran/bin/linux/ubuntu) jaunty/

```

# Grab the secure key
gpg --keyserver subkeys.pgp.net --recv-key E2A11821
# Add the key
gpg -a --export E2A11821 | sudo apt-key add -

# Add the correct repository from the website based on your 
# version of ubuntu.
# System -> administration -> Software sources
# Or use terminal to edit your /etc/apt/sources.list file.

# Install R
sudo apt-get update
sudo apt-get install r-base

```

---

