---
title: "how to have Java3D?"
date: 2010-02-03
forum: General Help
---

### Post by xieu90 on 2010-02-03
hi,
I want to learn Java3D and using Eclipse now
my java programs work, but when I run Java3D programms then there are full of errors (I think I dont have java 3D library or something is missing)

oem@oem-laptop ~ $ java -version
java version "1.6.0_15"
Java(TM) SE Runtime Environment (build 1.6.0_15-b03)
Java HotSpot(TM) Client VM (build 14.1-b02, mixed mode, sharing)

what should I do to get Java3D now?

---

### Post by xieu90 on 2010-02-04
dont know how, but it works now

1, go to synaptic and install
libjava3d-java
libjava3d-jni

2, download the newest version from
[https://java3d.dev.java.net/binary-builds.html](https://java3d.dev.java.net/binary-builds.html)

extract it and copy jar files to /usr/lib/jvm/java-6-sun-1.6.0.15/jre/lib/ext

copy the so files to /usr/lib/jvm/java-6-sun-1.6.0.15/jre/lib/i386

also 

use this one
Canvas3D myCanvas3D = new Canvas3D(SimpleUniverse
			.getPreferredConfiguration());
instead of 
Canvas3D myCanvas3D = new Canvas3D(null);

---

### Post by lightgiver on 2011-02-12
> **xieu90 said:**
> 

2, download the newest version from
[https://java3d.dev.java.net/binary-builds.html](https://java3d.dev.java.net/binary-builds.html)



link is dead, ill look for a new one

---

