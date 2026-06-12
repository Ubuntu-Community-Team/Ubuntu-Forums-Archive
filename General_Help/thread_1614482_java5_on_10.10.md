---
title: "java5 on 10.10?"
date: 2010-11-05
forum: General Help
---

### Post by gcbzzzz on 2010-11-05
why there's only java6 (jdk and jre) in ubuntu 10.10?

i need java5 for Android development.

is there a repository or should i bite the bullet and install from sun.com?

---

### Post by gcbzzzz on 2010-11-05
here's the direct link to java5-jdk update 22.

[http://java.sun.com/javase/downloads/5u22/jdk](http://java.sun.com/javase/downloads/5u22/jdk)

---

### Post by amasilaw on 2010-11-05
This one works: [http://blog.enea.com/Blog/bid/32050/Ubuntu-9-10-Java-5-and-the-Android-Open-Source-Project](http://blog.enea.com/Blog/bid/32050/Ubuntu-9-10-Java-5-and-the-Android-Open-Source-Project)
Actually use method 2 it's works perfect for me.
good luck

---

### Post by tja'hooker on 2011-10-28
> **amasilaw said:**
> This one works: [http://blog.enea.com/Blog/bid/32050/Ubuntu-9-10-Java-5-and-the-Android-Open-Source-Project](http://blog.enea.com/Blog/bid/32050/Ubuntu-9-10-Java-5-and-the-Android-Open-Source-Project)
Actually use method 2 it's works perfect for me.
good luck

Is there a different address to access these older versions of jdk,

thanks..

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
  404  Not Found [IP: 91.189.92.170 80]
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.170 80]

E: Some index files failed to download, they have been ignored, or old ones used instead

---

### Post by enkay009 on 2011-10-28
Method 2 from that blog seems to be how to install sun java from the ubuntu repos. If you want sun java, you may as well just download it from sun. They still host older versions on their site, but they only make it available if you create an account. It's free so it shouldn't be a hassle.

---

