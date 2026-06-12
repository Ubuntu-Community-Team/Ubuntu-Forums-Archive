---
title: "Adding Debian repositorys to Ubuntu"
date: 2010-08-21
forum: General Help
---

### Post by darkstarbyte on 2010-08-21
I have looked for a little while and was wondering if some one could give a Debian repository to add to my Ubuntu computer.

---

### Post by vince2678 on 2010-08-21
Add these to /etc/apt/sources.list:

deb [http://ftp.us.debian.org/debian](http://ftp.us.debian.org/debian) stable main
deb [http://ftp.us.debian.org/debian](http://ftp.us.debian.org/debian) testing main
deb [http://ftp.us.debian.org/debian](http://ftp.us.debian.org/debian) unstable main

OR

deb [http://ftp.(two](http://ftp.(two) letter country name).debian.org/debian (distro version) main

---

### Post by elliotn on 2010-08-21
Why wanna do that?

---

