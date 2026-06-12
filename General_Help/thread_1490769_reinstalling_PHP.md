---
title: "reinstalling PHP"
date: 2010-05-22
forum: General Help
---

### Post by Duckslammer on 2010-05-22
I need some PHP libs that don't come with the standard install - I assume that means I'll have to build PHP from source.  Can I use a package manager to download the source?  How? If I do, will it have the code for all the libraries?  Are there specific instructions for building and installing on ubuntu?

---

### Post by gordintoronto on 2010-05-22
Have you searched in Synaptic for the libs? I would be very surprised if you have to build from source just because you added some libs.

---

### Post by tgalati4 on 2010-05-22
What are the libraries in question?  If they are compatible with the default PHP version, then you can simply copy them to the appropriate directories.  If they are in the repositories, then add them with synaptic or apt-get.

apt-cache search PHP
apt-cache search thenameofyourspecificPHPlibrary

---

