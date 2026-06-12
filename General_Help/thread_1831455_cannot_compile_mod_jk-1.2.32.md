---
title: "cannot compile mod_jk-1.2.32"
date: 2011-08-23
forum: General Help
---

### Post by kalle_mod on 2011-08-23
Hi there

I had some trouble getting Apache2 and Tomcat7 to work together with mod_jk so I decided to wipe out tomcat and mod_jk and start all over with the newest versions.

I downloaded tomcat 7.0.20 and tomcat-connectors-1.2.32-src.tar.gz and uncompressed both. (tomcat is now installed in /etc/tomcat7 and runs fine on port 8080).

Then I tried to compile mod_jk from jeg source:

cd into native
./configure

fails with no apache given
no netscape given
configure: error: Cannot find the WebServer
./configure --with-apxs2=/usr/sbin/apxs2 gives the same result (after installing apache-threaded-dev with apt-get install)

I used to simply download the binary for linux from the apache website but they have chosen to stop compiling for *NIX systems :(

Can anyone help me through this problem?

---

### Post by kalle_mod on 2011-08-24
Btw. I'm running Ubuntu 8.04 :)

---

