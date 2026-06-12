---
title: "Php from Source -- How to tell APT its installed?"
date: 2011-12-09
forum: General Help
---

### Post by ghetto2ivy on 2011-12-09
I compiled php from source and have it working on the commandline and apache just fine. 

My problem is that when I try to install a package that uses php, like phpmyadmin, apt wants to install php packages to do it. I used checkinstall to create a deb and regsiter it, but it doesn't seem to matter.

(I compiled php 5.2, but phpmyadmin works fine with 5.2).

Any tips?

---

### Post by ghetto2ivy on 2012-01-01
Bump!

Can't believe that no one else has run into this, or that there isn't a way to do tell ubuntu that I built a dependency from source rather than installing from apt.

---

### Post by bodhi.zazen on 2012-01-02
This is the type of problem you run into if you install packages from source, outside of the package manager.

Sounds as if the package you built is not functioning properly, in particular the version information.

Take a look at your .deb and see what is in the control file

[http://www.debian.org/doc/manuals/maint-guide/dreq.en.html](http://www.debian.org/doc/manuals/maint-guide/dreq.en.html)

[http://developer.ubuntu.com/packaging/html/debian-dir-overview.html](http://developer.ubuntu.com/packaging/html/debian-dir-overview.html)

Most people who use Ubuntu do not install from source code, and you picked a complex package (php).

Why are you compiling php from source ?

---

### Post by ghetto2ivy on 2012-01-08
Thanks a ton for the lead. I've gotten closer, and it looks like it was an issue with the include directory and the php compiled from source.

I need to compile to get php 5.2 up and running with 11.10. All the other online tricks seem to have died when Karmic became unsupported. I have a php project that isn't 5.3 compatible, and is too big to make the shift any time soon.

Not quite resolved yet, I'll post when I'm sure of a resolution.

---

### Post by ghetto2ivy on 2012-02-04
FYI, I ended up simply pinning php to 5.2 using the old karmic sources. Since its not a production machine I can live with the fact that karmic stopped at 5.2.10 until we upgrade our app to be 5.3 compatible.

---

