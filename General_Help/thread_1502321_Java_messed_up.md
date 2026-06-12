---
title: "Java messed up"
date: 2010-06-05
forum: General Help
---

### Post by Nonno Bassotto on 2010-06-05
I just upgraded from 9.10 to 10.04, and I have an issue with Java.

Both tzdata and tzdata-java appear now as manually installed (which is not the case, they were just upgraded one minute before dist-upgrade) with the version 2010j-0ubuntu0.9.10

The version 2010i-1 is available, but if I force this version, Java (openjdk-6-jre) and all its dependencies are removed.

What is the current version of tzdata and tzdata-java in Lucid? I guess it is 2010i-1, so how do I restore it without messing up Java?

---

### Post by dino99 on 2010-06-05
sudo dpkg-reconfigure tzdata-java

---

### Post by Nonno Bassotto on 2010-06-05
Thank you, it worked!

---

