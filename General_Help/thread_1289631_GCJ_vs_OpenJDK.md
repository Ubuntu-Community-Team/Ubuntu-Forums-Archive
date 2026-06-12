---
title: "GCJ vs OpenJDK"
date: 2009-10-12
forum: General Help
---

### Post by Kismet on 2009-10-12
Can someone please explain to me why the Ubuntu team insists on still using GCJ. 

I have never found anything that doesn't work so far with OpenJDK, on the contrary several things are VERY buggy using GCJ. 

I install java-6-openjdk, and update-java-alternatives, yet some programs(eclipse, etc) still claim to rely on gcj. 

It's gotten to the point, I just let apt install gcj.
I then just goto /usr/lib/jvm, /usr/share/java and 'sudo rm -Rf 'xxxxgcjxx' ...etc to delete all references to it. Everything still works fine, and apt is happy because it THINKS gcj is installed.

Why oh why does anyone choose gcj over openjdk?

---

### Post by cb951303 on 2009-10-12
AFAIK, in Karmic you can choose to install eclipse with gcj or openjdk

---

