---
title: "Updating R to the latest version"
date: 2012-04-19
forum: General Help
---

### Post by hojjat on 2012-04-19
I want to update R on ubuntu to the latest version (which at the time is 2.15.0). The version included in the Ubuntu Oneiric software repos is 2.13.0. I tried adding a CRAN source to my software sources as described [here](http://cran.stat.ucla.edu/bin/linux/ubuntu/), but after doing so and running apt-get update and apt-get upgrade, R is not upgraded to a new version. I can't find any information about a PPA for R either. Any advise is appreciated.

---

### Post by dniMretsaM on 2012-04-19
What is the output of this command:
```
apt-cache showpkg r-base
```

---

### Post by hojjat on 2012-04-26
```

Package: r-base
Versions: 
2.13.1-1 (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_oneiric_universe_binary-i386_Packages) (/var/lib/dpkg/status)
 Description Language: en
                 File: /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_oneiric_universe_i18n_Translation-en
                  MD5: e8de27c34fdd57ca1c4480d402910df7
 Description Language: 
                 File: /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_oneiric_universe_binary-i386_Packages
                  MD5: e8de27c34fdd57ca1c4480d402910df7


Reverse Depends: 
  texmacs,r-base
  science-numericalcomputation,r-base
  science-meteorology,r-base
  r-doc-info,r-base 1.4.1-1
  r-doc-html,r-base 1.4.1-1
  r-base-html,r-base 1.4.1-1
  r-base-core,r-base 1.4.1-1
  med-physics,r-base
  ess,r-base
Dependencies: 
2.13.1-1 - r-base-core (2 2.13.1-1) r-recommended (5 2.13.1-1) ess (0 (null)) r-doc-info (16 (null)) r-doc-pdf (0 (null)) r-base-html (0 (null)) r-doc-html (0 (null)) 
Provides: 
2.13.1-1 - 
Reverse Provides: 

```

---

### Post by PGScooter on 2012-04-26
Go to [www.r-project.org](www.r-project.org) > download R > choose a mirror > download R for linux > Ubuntu

For example,
[http://cran.cnr.berkeley.edu/bin/linux/ubuntu/](http://cran.cnr.berkeley.edu/bin/linux/ubuntu/)

All of the information you need is here. They are really good about updating the repos a few days after every release and minor release.

For the future, R questions are usually best answered in the Education & Science forum.

Did this work for you?

---

### Post by hojjat on 2012-04-26
That is exactly what I did. I am using a different source (not berkeley) but it shouldn't matter.

---

### Post by PGScooter on 2012-04-26
> **hojjat said:**
> That is exactly what I did. I am using a different source (not berkeley) but it shouldn't matter.

I'm sorry for not reading your post more carefully.

Did you do this part pasted below? Make sure there were no errors after each of the commands. Then do sudo apt-get update and again check to make sure no errors. Then post back.

The Ubuntu archives on CRAN are signed with the key of "Michael Rutter <marutter@gmail.com>" with key ID E084DAB9. You can fetch this key with

   gpg --keyserver keyserver.ubuntu.com --recv-key E084DAB9

and then feed it to apt-key with

   gpg -a --export E084DAB9 | sudo apt-key add -

Some people have reported difficulties using this approach. The issue was usually related to a firewall blocking port 11371. An alternative approach is to search for the key at [http://keyserver.ubuntu.com:11371/](http://keyserver.ubuntu.com:11371/) and copy the key to a plain text file, say key.txt. Then, feed the key to apt-key with

   sudo apt-key add key.txt

---

### Post by hojjat on 2012-04-26
Yes. As a matter of fact, without that last part, *apt-get update* gives you an error message.

---

### Post by PGScooter on 2012-04-27
> **hojjat said:**
> Yes. As a matter of fact, without that last part, *apt-get update* gives you an error message.

But it doesn't give you an error when you do that last part? Have you tried using a different mirror? This is strange. I've followed those directions on 5 different systems and never had a problem.

---

### Post by hojjat on 2012-04-27
Right now, I'm updating the machine to Precision (Ubuntu 12.04). Once finished, I expect to have version 2.14 installed (it comes with Precision). I will then try a different mirror to see if I can upgrade to 2.15

---

### Post by PGScooter on 2012-04-27
> **hojjat said:**
> Right now, I'm updating the machine to Precision (Ubuntu 12.04). Once finished, I expect to have version 2.14 installed (it comes with Precision). I will then try a different mirror to see if I can upgrade to 2.15

OK, I just installed 12.04 and I just ran the following three lines (the first I ran after sudo su)
```

echo "deb http://cran.mirrors.hoobly.com/bin/linux/ubuntu precise/" >> /etc/apt/sources.list
gpg --keyserver keyserver.ubuntu.com --recv-key E084DAB9
gpg -a --export E084DAB9 | sudo apt-key add -

```

and then a simple sudo apt-get install r-base. And that was it.

---

