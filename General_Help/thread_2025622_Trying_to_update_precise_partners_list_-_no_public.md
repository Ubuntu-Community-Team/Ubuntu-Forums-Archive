---
title: "Trying to update precise partners list - no public key"
date: 2012-07-14
forum: General Help
---

### Post by Gusss on 2012-07-14
Hi -
I have logged into gedit as root. I am following the instructions in this page precisely to try and add a url to the precise partners list :

[http://cran.r-project.org/bin/linux/ubuntu/](http://cran.r-project.org/bin/linux/ubuntu/)

my precise partners list looks like this :

> deb [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/) precise main
deb-src [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/) precise main
deb [http://stat.ethz.ch/CRAN/bin/linux/ubuntu](http://stat.ethz.ch/CRAN/bin/linux/ubuntu) precise/

I keep getting this response no matter which mirror I use :

> W: GPG error: [http://stat.ethz.ch](http://stat.ethz.ch) precise/ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 51716619E084DAB9


where am I going wrong ?

---

### Post by plucky on 2012-07-14
> where am I going wrong ? 

You need to add the key 

From a terminal run the two commands to add the key
```
gpg --keyserver hkp://subkeys.pgp.net --recv-keys 51716619E084DAB9
gpg --export --armor 51716619E084DAB9 | sudo apt-key add -
```

Then run ```
sudo apt-get update
``` to reload the list files.
you should now be able to install from those repositories.


Good luck

---

