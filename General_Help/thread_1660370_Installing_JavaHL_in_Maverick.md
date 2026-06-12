---
title: "Installing JavaHL in Maverick"
date: 2011-01-05
forum: General Help
---

### Post by daredevil82 on 2011-01-05
Hi all,

I'm trying to get Subclipse working in Eclipse Galeilo, and to do that I have to install the JavaHL library.

I installed the library using sudo apt-get install libsvn-java, but the eclipse.ini file has to be modified to take in the new library as an argument.

First change to the ini file was -Djava.library.path=/usr/lib/jni/, which produced the errors 
"no libsvnjavahl-1 in java.library.path"
"incompatible javahl library loaded. 1.3.x or later required."
*according to the install printout, version 1.6.12 was installed.

So, I added libsvnjavahl-1.so to the file path above, and produced the following errors:
"no libsvnjavahl-1 in java.library.path"
"no svnjavahl-1 in java.library.path"
"no svnjavahl in java.library.path"

What's going on here?

---

