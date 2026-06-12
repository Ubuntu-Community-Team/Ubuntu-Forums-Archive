---
title: "Java Help!?"
date: 2010-06-26
forum: General Help
---

### Post by superman37876 on 2010-06-26
Hi. I'm trying to install sun-java6-jre as a program needs it to run. When I try to install I get the error below. Any ideas? I'm new to Ubuntu...

sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-jre has no installation candidate

---

### Post by timvoet on 2010-06-26
The sun jdk packages have been moved out of the standard repos and into the partner repositories

you can enable it this way

add-apt-repository “deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner”

---

### Post by superman37876 on 2010-06-26
Thanks. When I try that I get the following:

Error: need a repository as argument

Update: I went into the Software Sources and added the &#8220;deb [http://archive.canonical.com/](http://archive.canonical.com/)  lucid partner&#8221;. Updated the system and now it seems to be installing. Thanks for the help!

---

