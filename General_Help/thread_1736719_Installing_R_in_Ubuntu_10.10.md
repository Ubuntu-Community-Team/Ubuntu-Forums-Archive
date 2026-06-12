---
title: "Installing R in Ubuntu 10.10"
date: 2011-04-22
forum: General Help
---

### Post by amathew on 2011-04-22
I'm using the instruction here to install the latest version of R:
[http://cran.r-project.org/bin/linux/ubuntu/](http://cran.r-project.org/bin/linux/ubuntu/)

I add the following line to end of /etc/apt/source.list

deb [http://cran.wustl.edu/bin/linux/ubuntu](http://cran.wustl.edu/bin/linux/ubuntu) maverick/


However, I get the following error message when I run sudo apt-get update.

GPG error: [http://cran.wustl.edu](http://cran.wustl.edu) maverick/ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 51716619E084DAB9


How can I fix this?

---

### Post by wojox on 2011-04-22
Run these two commands in the terminal:

```
gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 51716619E084DAB9
gpg --armor --export 51716619E084DAB9 | sudo apt-key add -
```

---

### Post by amathew on 2011-04-22
That command doesn't work.

$ gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 51716619E084DAB9
gpg: requesting key E084DAB9 from hkp server wwwkeys.eu.pgp.net
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error



I tried the following, 

$ gpg --keyserver keyserver.ubuntu.com --recv-key 51716619E084DAB9
gpg: requesting key E084DAB9 from hkp server keyserver.ubuntu.com
gpg: key E084DAB9: "Michael Rutter <marutter@gmail.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

still get the error when i update:

GPG error: [http://cran.wustl.edu](http://cran.wustl.edu) maverick/ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 51716619E084DAB9

---

